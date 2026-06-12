---
title: "Acer Aspire 9500  Model AS9502WSMI"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by Neg127 on 2006-06-14
I have an Acer Aspire 9500 Model AS9502WSMI and it is working fantastic under Drapper 6.06.  There are a few things that are not configured correctly out of the box, but it is pretty minimal.

The video is the biggest part, you have to use safe mode in order to get xorg to function correctly.  Well It may not have been xorgs fault, I just had a blank screen so it may not have had the correct resolution and refresh rates etc.  I'll test it later to night after work.

The hardware specs are.   Intel Centrino Processor 740 (2MB L2 cache, 1.73GHz, 533MHz FSB); 1.5GB DDR2 533 SDRAM; 100GB hard drive; integrated DVD-Super Multi double-layer drive; 5-in-1 card reader; 17.0" WXGA+ (1440 x 900) TFT display, Acer CrystalBrite Technology; ATI MOBILITY RADEON X700 graphics, 128MB DDR; 802.11b/g WLAN, gigabit LAN, V.92 modem. 

I'll post some more specifics in the exact hardware a little later.  Its wonderful to have hardware that is so new fully supported under linux.  I have had issues in the past in configuring my notebooks to run linux correctly.

I'm going to work on getting the few issues worked out later to night and I will post an update.  Get my video working correctly with full opengl and glx support, get my centrino processor and speed step to function correctly and those will be two of the big things.

Updates to come.

---

### Post by Neg127 on 2006-06-15
Just a small update.

I was able to get my ATi Radeon Mobile X700 to function 100% correctly using the post from [HERE]("http://www.ubuntuforums.org/showthread.php?t=191944").  So if you are having any troubles with your ATi cards and getting 3d acceleration take a look at the thread.  Also once I installed the drivers and switched over to them all the correct resolutions for my monitor worked flawlessly.

I still cannot confirm whether my firewire functions correctly, I do not have any firewire devices to test it with.  I am also still looking in to the IR built in to the notebook.  All the function keys are working correctly.  I am able to dim the monitor gamma, mute the sound, disable the track pad, turn off and on the LCD, and all the other functions.

All in all I would say this notebook is supported very well under 6.06, now how do I get the information entered in the notebook hardware compatibility list?

---

### Post by tombott on 2006-10-18
Hi,did you manage to get the card reader to work?
I'm having no joy with that,but everything else works a dream!

---

### Post by munckfish on 2006-10-20
Hi

I've got an Aspire 9504WSMi. I'm also really happy with the way Dapper runs on it. However, I've still got a list of stuff that I've not got setup properly yet. In particular I'm about to get working on the Arcade buttons on the front panel plus the other hotkeys, and the S-Video/TV-Out. If I find anything useful I can post it here.

Has anyone got any good links or tips on setting that stuff up?

Cheers

---

### Post by faxdd on 2006-11-16
Hi...I'm a new linux user. I've installed ubuntu on Acer Aspire 9504WSMi. I have problem to start with X GUI. My video card is ATI X700. I tried all, but nothing!Also because on this machine where I installe ubuntu, I don't have a net,so I can't download updates, how many posts indicate to do.

Can someone help me?

Thanks of all

---

### Post by munckfish on 2006-11-16
Hi faxdd

I had this problem with Ubuntu on the 9500 . To get the default open source ATI X drivers to work I had to tweak /etc/X11/Xorg.conf. I wrote instructions on my blog to do this with the Breezy LiveCD ages ago so I'm not sure the method still works cause on Dapper I just changed over to using the binary drivers. Anyhow here's the post:

[http://munckfish.net/blog/archive/2006/02/07/ubuntu-on-acer-aspire-9500/](http://munckfish.net/blog/archive/2006/02/07/ubuntu-on-acer-aspire-9500/)

The quickest and easiest solution however, is to use the [ATI binary drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), as things will 'just work'. But that will of course require access to the online repositories or at least a way to grab the required packages from the internet for later offline installation.

Cheers

---

### Post by faxdd on 2006-11-17
Hi,thank you for reply. The problem is that I don't have a connection on this maschine where I installed Ubuntu (and this is another problem I have,because I can't reach to configure network!), so I can't download binary driver ATI directly. Can you say to me where I can download them from another machine and how I can install on ubuntu off-line?

PS.Can you help me to configure a network, too? I have a LAN with a fixed IP, no server DHCP. I think to configure it good,set the IP of ethernet 0,but when I open browser web it can't visulize anything....:-k 

Thank you very very much!

---

### Post by faxdd on 2006-11-17
PS.I don't say that I will work whit UBUNTU 5.10

---

### Post by munckfish on 2006-11-17
Hi faxdd

Can you answer a few questions so I can decide how to help you?

1. What version of Ubuntu are you using? 
  - Dapper 6.06
  - Edgy 6.10
  - Other?

2. Have you installed Ubuntu on your machine yet or are you testing with the live cd?

3. When you boot your machine into Ubuntu do you get a blank screen when it's finished or a command shell or what?

---

### Post by faxdd on 2006-11-17
Hi,so:

1)The version is 5.10
2)Just installed
3)When I boot see the login page, normally, but to do this I had disabled ATI driver and used standard VESA driver. 

I hope that I'm clare...sorry if I don't.

So I have this 2 problem at moment:
1) Configure exactly the ATI driver
2) Configure LAN

---

### Post by faxdd on 2006-11-20
Please someone can help me with this two problem?

1)Configure exactly ATI driver
2)Configure LAN

Thanks a lot!;)

---

### Post by munckfish on 2006-11-20
Hi faxdd

1) Networking:

You need to configure your network card to use a static IP? Ok, try this:

[LIST=1]
[*]Start the Networking Utility: System > Administration > Networking ([screenshot]("http://www.phoronix.net/image.php?id=218&image=ubuntu_breezyc2_04_lrg")). It'll prompt you for your password.
[*]When the dialog appears select "Ethernet connection" then 
[*]Click the "Deactivate" button. If it is not clickable/enabled don't worry.
[*]Click the "Properties" button on the right. You will see the "Interface Properties" dialog.
[*]Make sure the "Enable this connection" checkbox is ticked.
[*]Set configuration to "Static IP Address". This will enable the rest of settings fields on the form.
[*]Enter your network settings and click ok. The dialog will close, and you will see the "Network Settings" dialog again.
[*]_Make sure your network cable is plugged in_.
[*]Make sure "Ethernet connection" is still selected then click on the "Activate" button. If everything is configured correctly you should see a progress bar for a short while then it should disappear fairly quickly.
[/LIST]

2) Setting up the ATI driver. Now that you have an internet connection, I recommend trying the following HOWTO: [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). 

There are lots of help documents available for all sorts of configuration available on [https://help.ubuntu.com/](https://help.ubuntu.com/) and [http://doc.gwos.org/](http://doc.gwos.org/).

I hope you get on ok. :)

---

### Post by faxdd on 2006-11-20
Thanks a lot!
I'll try these instructions tomorrow and refer you results.
Only a last question: where I must set the DNS ?? because in the passes that you indicate me,I can set only IP and other information,but non DNS.

Excuse me for continuos question,and thank you for helping me!:)

---

### Post by munckfish on 2006-11-20
For DNS - explore the Networking utility. DNS config is done there, you'll find it.

---

