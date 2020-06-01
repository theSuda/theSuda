---
toc: true
layout: post
comments: true
description: You won't know what you were missing until you get one..
categories: [markdown]
title: Every developer should have a Raspberry PI
---

## Raspberry... what?

If you don't know what a [Raspberry Pi](https://www.raspberrypi.org/) is, you should check it out. It's a single board computer barely bigger than a credit card in size. It can run many operating systems like Raspbian, Ubuntu and Windows 10 IoT core. To use this tiny computer, all you need is a micro SD card and a power supply. For most use cases you will never have to connect a keyboard or mouse to the pi. You can just set it up and access remotely from your personal computer. Raspberry Pis are a favorite tool of most DIY enthusiasts. Even if you don't plan to do any fancy DIY projects at home, you can still find some use for a Raspberry Pi. 
Some notable examples: An ad blocker at router level, Minecraft server, Plex streaming station, self hosted cloud, temperature monitor, smart mirror and much more. More details on some of these projects later below.

_This article was updated on 3-Jan-2020_
<!--excerpt-->
## Basic setup guide:
### Hardware 
1. Buy **a Raspberry Pi**. [Check here](https://www.raspberrypi.org/products/) for retailers. Check your local stores like Fry's, Micro Center, Target and even some Walmart stores have it. There are multiple models of pi. 
  * **Raspberry Pi Zero W**: A very tiny pi that costs $10. Best for light use. 
  * **Raspberry Pi 4 Model B**: A very powerful latest version of pi. Comes in variants 1gb, 2gb and 4gb. Well suited for many home server applications. See below. Costs from $30 to $60 depending on model.
  * **Raspberry Pi 3 Model B+**: Previous pi model before they launched pi 4. If you can't get your hands on a model 4, go with 3B+. It still holds well for many applications. Should cost around $25-30 now.
 
2. **A micro SD card**. This will be your main system disc. 16gb works fine but I recommend at least 32gb. The cards have gotten cheap so 32gb should cost like [$6.49 here](https://smile.amazon.com/dp/B06XWN9Q99/).

3. **A card reader/laptop with SD card reader**. This is necessary to install operating system on the SD card. You can buy cards with pre-installed OS but what's the point of tinkering if you don't do it yourself?

4. **A power adapter**. Depending on which Pi you have, you will either need a micro USB or a USB-C power source. Majority of Android phone chargers will do the job in a pinch but I recommend buying a proper power adapter. All the electronics stored mentioned above should have them along with Pi.

### Base Software/OS setup
There are multiple linux distros available for Raspberry Pis. Most commonly used OS for a pi is Raspbian. It is developed by Raspberry Pi foundation and has most users. Installing this OS is actually very simple. 

1. Download the OS image. Raspbian can be downloaded from [this page](https://www.raspberrypi.org/downloads/raspbian/). Choose Rasbian Lite (no GUI, only base OS) if you plan to use the pi for non visual stuff. You never have to connect a monitor to pi unless your project needs a screen. So it's always a good idea to start with Raspbian lite.

2. Windows users download one of these tools: Win32DiskImager, Rufus. These are used to install the OS image to your SD card.

3. Plug in your micro SD card. Open Win32DiskImager. Select the OS image downloaded in step 1 above, make sure the drive selected by the tool is the SD card. Hit 'Write', accept warnings and stuff. Takes around a minute or so to write the SD card.

4. **VERY IMPORTANT DON'T SKIP THIS STEP**
Detailed instructions [here](https://desertbot.io/blog/headless-raspberry-pi-3-bplus-ssh-wifi-setup/). Quick version:
On your desktop, create following files.
   * An empty file named 'ssh' without any extension. Not even txt. 
   * Another file named `wpa_supplicant.conf` and paste following in the file (update your wifi network name and password of course):
     ```
     country=US
     ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
     update_config=1
     
     network={
         ssid="NETWORK-NAME"
         psk="NETWORK-PASSWORD"
     }
    ```
5. Now remove the car from your computer, put it in the pi. Connect the pi to the power supply. Give it a minute to boot for first time. Find out what IP got assigned to the PI using your router interface. If all goes well, you will see the pi connected to your wifi. Now you can SSH into the pi. Windows 10 has now built in SSH so you don't need any external tools. 
Just open cmd and type `ssh pi@<<ip-address>>`. Default username for Raspberry pi is `pi` and password is `raspberry`. Change the password once you login. 

## Some projects
Now we have it up and running, here are few projects you can do with your Raspberry pi:

* Run a [PiHole](https://pi-hole.net/) ad blocker for your network
This is first project I did with a Raspberry pi zero. PiHole If you live near a micro center, you can get a PI Zero W (wifi version) for $10 ($5 when on sale).  

* A [Plex](https://www.plex.tv/) media server: Attach a USB drive filled with your movies, photos and videos to the pi. [Make it auto-mount](https://www.raspberrypi.org/documentation/configuration/external-storage.md). Install Plex media server and now you can cast your own library of movies to your TV using Plex mobile app. It's like having your own Netflix. It has features like automatic subtitle downloads, remote access from outside your home etc. 

* Host a website: There are many tutorials online about how to host a website on your pi. Though it is always better to just get a commercial server package than self hosting a website. But you can always just use Pi as your testing server.

* Smart Mirror: A digital overlay on a mirror that shows you weather, news and your meetings etc. If you check [Raspberry Pi subreddit](https://www.reddit.com/r/raspberry_pi/) or [Pi projects subreddit](https://www.reddit.com/r/RASPBERRY_PI_PROJECTS/), you will see someone posting a Smart Mirror build every week.

* A Minecraft server if you are into that sort of thing.

* Personal Cloud: You will need to research this a bit. There are many open source and free personal cloud distros available. [OpenMediaVault](https://www.openmediavault.org/) works great on Raspberry Pi.
