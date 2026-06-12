---
title: "Graphical error when booting ubuntu ultimate 1.5 on hp pavilion dv6000"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by kylewhite on 2008-02-04
"Cannot start x server (your graphical interface)"
when booting the live disk i had to boot in safe graphics mode, otherwise i would get this error. after installing in safe graphics mode, it lets me boot once without the live disk with no problems, but if i reboot after that it gives me the same "cannot start x server" error.

---

### Post by nzruss on 2008-02-05
I'm having a similar problem, just getting started on this install. (the HP dv6000 is by far the hardest install i've ever had to do)

This post is a good starting point:
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

But see my post below for more information.

---

### Post by nzruss on 2008-02-06
Ok, got it sorted last night. (On an HP - AMD Pavilion TK-57 Laptop (Model: dv6704nr) or more commonly called a Pavilion dv6000.It has "NVIDIA GeForce Go 7150M (UMA) graphics with up to 799MB total available graphics memory; S-video TV-out" - I have not confirmed operation of the s-video or tv out)

**Ubuntu 7.10 **

Here is what you can try (based on the info from that thread I referenced in the Post above, and my success).

1 - Boot into safe graphics mode (boot normally and when it prompts that x will not load, and gives you the option to continue, you continue - this should be safe mode.)

2. Update your system (just wait and use the normal update taskbar icon, or use "sudo apt-get update" and "sudo apt-get upgrade" at the (applications, accessories, terminal) command line.

3. Open firefox and download the "Envy" Application. This application does not appear to be in any of the default Ubuntu repo's, so all the precautions and disclaimers with installing packages from an unknown source apply. I had no problems with it.

[INDENT][INDENT][INDENT][I][SIZE="2"]""Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you" [/SIZE][/I][/INDENT][/INDENT][/INDENT]

4. So download envy (click this link) [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb) 

[INDENT](It is from this page here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)).[/INDENT]

4. And open with the default application, and click "Install package".    It should ask to install dependencies, so click OK and let them install. I had no problems here. Once all that is complete:

5. Click >applications>system tools>envy
 [INDENT]Screenshot: [URL="http://www.personal.psu.edu/users/n/p/npl108/Screenshot-Envy.png"] ... here...[/INDENT]

[/URL]6. Select the appropriate driver you want to install (mine was "install the nvidia driver").   It will do a bunch of stuff automatically, just wait and let it do its thing. You will then be asked to restart your machine. 

NOTE:  Once you've restarted it MAY load properly. It MAY not. You might get the same "cannot start x" and offer you safe mode as what happened to me. The thread reference above, it took 3 tries to get it going. 

What I did : (i'm not sure that all these steps are required, But they worked for me while trying to get it going. You may try any combo of the steps below in a different order and have the same or different success.)

a. Started again in safe mode
b. Selected >system>administration>restricted drivers> selected "NVIDIA"
c. Restarted computer. (it only offered safe mode again)
d. then selected >Applications>system tools>Envy
e. Selected "uninstall nvidia driver"
f. selected "install nvidia driver"
g. rebooted

WA-LA!!! it stuck and I have full Nvidia graphics with desktop effects!

I hope this helps.

---

### Post by Muscar on 2008-02-06
When i contyinus to get to safemode it just brings me to the nongraphical part

---

### Post by nzruss on 2008-02-06
I just re-read your original post. - and I'm sorry but I just realized you're trying to get the live CD going...  

I wasn't able to get my live CD to work, so took a leap of faith that I'd be able to get the actual install working.  I used the "Alternate" install disk and just went for it. When it gets to the 'partition' section, I chose the 'resize' option. (it did take a while to resize the vista partition - with no progress bar movement), so my laptop is now dual boot. I had already made the vista restore disks so if it all went horribly wrong I could use those to get me back to square one. 

Have you installed Ubuntu on any other machines before? Are you comfortable installing your machine dual boot? - if you want to keep going then I'm happy to help.  I'm not an expert, but I'm happy go guide you through as much as I can - seeing as I'm doing the same thing also and i'm comfortable in my ability to get it all working.    I expect to have the wireless going tonight. I've already confirmed most of the functions on the IR remote work with Ubuntu also.

---

### Post by Dittie on 2008-02-06
Pardon my stupidity, I'm having the same problem with the dv6704nr that I just picked up today.. what is the alternate cd?

---

### Post by nzruss on 2008-02-06
Hey, welcome to the thread. 

on the [download page]("http://www.ubuntu.com/getubuntu/download"), there is a bit at the bottom which says:

"Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

That is the alternate. Let me know where you get stuck and we'll try to get all three of us through this in one piece!!!!

---

### Post by Dittie on 2008-02-06
Great, thanks! I'm downloading it now. i'll let you know how things go tomorrow :)

---

### Post by nzruss on 2008-02-07
Ok, Hope you've got the display working properly by now..... 

Now I'm working on getting the wireless going... Ive tried a couple of methods, but no luck... I'll keep trying and post back when i get it.

Let me know how you get on with the install dittie.

---

### Post by Dittie on 2008-02-07
i'm actually having some problems with the install. i think the cd i made may be bad so i am downloading and making a new one. it stops progress on installing files at 85% for some reason.

up until that point though, it was going great :)

---

### Post by Dittie on 2008-02-07
BTW, try using ndiswrapper for the wireless if you haven't yet.

---

### Post by nzruss on 2008-02-07
are you connected to an ethernet cable while doing the install? I've found ubuntu likes to be connected for some reason. 

I also figured the wireless out. Will post below.

---

### Post by nzruss on 2008-02-07
While a little off topic for this thread, I also managed to get the wireless going on Ubuntu 7.10 

This is on an HP - AMD Pavilion TK-57 Laptop (Model: dv6704nr),  or more commonly called a Pavilion dv6000. It has "NVIDIA GeForce Go 7150M (UMA) graphics with up to 799MB total available graphics memory; S-video TV-out" -  I have not confirmed operation of the s-video or tv out)

The network card is listed as a:
> 
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.


1.   Dowload the latest windows driver for the wireless card from here:[ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip)

2. select "open with archive manager"
     once the folder is opened, double click the Atheros folder, then double click the 'HR2H01ww.zip' folder.    That should have opened a new window with archive manager. 

3.  Click 'extract', then Select "create folder" and type "Atheros" then hit the enter key (to create that new folder) .   This will put these new drivers on your desktop in a folder called "Atheros". (and it should open that folder in a new window)

(you can go ahead and close those extra windows now)

4.  Now disable the restricted drivers that ubuntu uses: 
     click:   system > administration> restricted driver managers, 
     then uncheck the atheros driver to disable it. Ubuntu will require you to do a restart so go ahead after you have bookmarked this page or copied the instructions to your Atheros folder.)

5. Welcome back: Open synaptic package manager 
     system> administration> synaptic
     search for "ndiswrapper" and install all three results  - (ndiswrapper-common, ndiswrapper-utils-1.9, and ndisgtk) 

6. Now to install the windows driver, click:
system > administration > windows wireless drivers
select "install new driver" and browse to the Atheros folder you created. 
select the file "NET5211.inf" and click install.
It should show up as "hardware present: yes"

7. After you have done this, verify that you have installed the driver, and it is being recognized correctly:   Open the terminal and type 
```

ndiswrapper -l

```
If it is installed correctly, it should look something like this:
> 

net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)


8.  Now we have to make sure the restricted driver ubuntu installed is blacklisted by typing/pasting:
```

echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist

```
9. Then make sure ndiswrapper starts at boot time

```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

```

10. Now restart your computer and you should have the wireless option in your network manager icon. 

Mine works perfectly - I just clicked network manager and chose my wireless network. Others have reported problems with the wireless inactive switch, but mine seems to work in the correct sense and I've had no problems. The light will remain orange though. (you can still turn off wireless with the switch, and it does turn off correctly.)

My post is based off this thread [http://ubuntuforums.org/showpost.php?p=3984855&postcount=6](http://ubuntuforums.org/showpost.php?p=3984855&postcount=6)
Thanks to those that posted there.

---

### Post by Dittie on 2008-02-08
Hey

All installed, got the graphics card working wonderfully thanks to your little walkthrough :)

Having some trouble with the wireless. But I think that's my fault and notthat of your instructions. 

Great work and thanks a bunch!

---

### Post by bluefox83 on 2008-03-01
I am running the HP Pavilion dv6000 laptop with the  AR5006EG 802.11 b/g Wireless PCI Express Adapter in the X86 version of gutsy, and I followed your directions to the tee and network-manager can SEE my wireless network, but try as i might, i cannot get it to CONNECT to it. Let me know if there is any info you need to help diagnose.

---

### Post by bluefox83 on 2008-03-07
UPDATE: I have decided it will be far easier to just use the 32 bit version of ubuntu since i can't get the 64 bit wireless driver to work.

---

### Post by nzruss on 2008-03-07
sorry I didnt get to reply to your previous post. Yeah, the 32bit works a treat. 

Only issue I have - which i discovered last night is that when you plug headphones in, the speakers still go... 

Not high on my priority, but will be looking for a solution...

Real shame that a big company lik HP/Compaq doesnt support Linux/Ubuntu better with their hardware. Surely the cost of employing a handfull of driver writers (even restricted) is going to make more than their money's worth in sales    /rant.

Edit: I found the solution to the sound here: 
[https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr)#head-c9292451b0fffef20ae7ab3af304768d2d08c6b3](https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr)#head-c9292451b0fffef20ae7ab3af304768d2d08c6b3)

---

### Post by kylewhite on 2008-03-21
Thank you very much. I'm downloading the alternate install disk right now and hope to have it up and running soon. I lost track of the thread for a bit, and apologize for not responding. :]

---

