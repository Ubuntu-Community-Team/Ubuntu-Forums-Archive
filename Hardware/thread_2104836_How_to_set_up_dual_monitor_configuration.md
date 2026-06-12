---
title: "How to set up dual monitor configuration?"
date: 2013-01-14
forum: Hardware
---

### Post by alaska12 on 2013-01-14
Hi guys, I'm a bit confused about how dual monitor management works in kde. 
My hardware is: asus 1215b netbook, ATI radeon HD 6310 graphic card, native monitor resolution:1366x768 + external monitor 23" lg IPS234V 1920x1080

There are 3 utilities on my netbook that can influence monitor's configuration: amdcccle (fglrx), krandr and jupiter (alternative power manager). 

My issue comes when I boot the system without connecting the external monitor: the grub screen is ok, but the splash screen is still set on 1920x1080. The system seems to fail in recognizing the netbook's monitor's native resolution. Result: I can't see login options... (Anyway I can still log in, but I must do it... "blindly"!)

Any idea on how to solve this?

Actually I would like to the computer to automatically detect which resolution to apply just from the beginning, like windows 7 does. My instinct says that I should tell the graphic card to load the configuration file before the splash screen, but I absolutely don't know how to achieve this (I don't even know how this configuration file is called, nor where it's stored...).

Finally I'm not so sure that the three utilities I listed above can actually "live" together in the same enviroment. Do they interfere with each other?

Can somebody help me? Thanks!

---

### Post by Hugh Mulqueen on 2013-01-15
When I have problems with my graphics drivers I have to go Ctrl+Alt+F1...F6 that is press Ctrl+.. etc. and F1 for example and you will be taken to the command line logon screen. Login and use:

1. **ls** or **pwd** to where your driver software is.

2. I'd say you'll need to get the propeitary driver download the latest here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

3. Download the driver and extract with:
**unzip file.zip -d destination_folder**

or if your in the folder already just
**unzip amd-driver[Tab].zip**

Use the Tab key to use auto-complete.

4. To get into the root account:
**sudo -i**

5. **sh {amd-driver...}.sh**

That should bring you up to speed. 

I'd advize that you download the installation package first to a USB stick and have gcc installed before you get the driver:
[B]
sudo apt-get install build-essential[/B]

You should be fine after that just sounds like your hardware isn't supported yet with the open source driver. 

Any more questions, don't hesitate to ask.;)

P.S. After installation **reboot** the computer with that command. And to get out of the CLI terminal use Ctrl+Alt+F7 and that should get you back to the desktop.

---

