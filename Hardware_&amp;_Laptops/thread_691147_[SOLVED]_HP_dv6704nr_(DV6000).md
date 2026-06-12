---
title: "[SOLVED] HP dv6704nr (DV6000)"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by nzruss on 2008-02-08
**Blank display or wireless issues on your dv6704nr?**

Here are the steps I used to get the nvidia drivers loaded an HP - AMD Pavilion TK-57 Laptop (Model: dv6704nr) or more commonly called a Pavilion dv6000.It has "NVIDIA GeForce Go 7150M (UMA) graphics with up to 799MB total available graphics memory; S-video TV-out" - though I have not confirmed operation of the s-video or tv out)

**Ubuntu 7.10 -i386 (32 Bit)  ** (Some users have reported problems with the 64bit install on this hardware.)


Here is what you can try to get your video drivers loaded, based on my success.

1 - Backup your windows system using the 'recovery disk creation' tool, if you have not done so already. Then using the **[Alternate Install Disk]("http://mirrors.gigenet.com/ubuntu/gutsy/ubuntu-7.10-alternate-i386.iso")**, do an install - and I found I had better success with the network ethernet connected than without.  During the install, you should be faced with the option to boot into safe graphics mode.  (i.e boot normally and when it prompts that x will not load, and gives you the option to continue, you continue - this should be safe mode.) If you get a blank screen, press CTRL-ALT F1 and log in and do step 2. 

2. Update your system (If you're in safe mode, just wait and use the normal update taskbar icon, or if you're at the command line use "sudo apt-get update" and "sudo apt-get upgrade". It will take a few minutes to do the updates. - it may require you to restart - no problems there. (if you're logged in at the console (CTRL-ALT F1), then type "sudo shutdown -r now" to reboot).

3. All going well, you are now in safe mode, and can open firefox. So open firefox and download the "Envy" Application. This application does not appear to be in any of the default Ubuntu repo's, so all the precautions and disclaimers with installing packages from an unknown source apply. I had no problems with it.

[INDENT][INDENT][INDENT][I][SIZE="2"]""Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you" [/SIZE][/I][/INDENT][/INDENT][/INDENT]

4. So download envy, available at this link:   [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb) 

[INDENT](It is from this page here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)).[/INDENT]

4. And open with the default application, and click "Install package".    It should ask to install dependencies, so click OK and let them install. I had no problems here. Once all that is complete:

5. Click >applications>system tools>envy
 [INDENT]Screenshot: [URL="http://www.personal.psu.edu/users/n/p/npl108/Screenshot-Envy.png"] ... here...[/INDENT]

[/URL]6. Select the appropriate driver you want to install (mine was "install the nvidia driver").   It will do a bunch of stuff automatically, just wait and let it do its thing. You will then be asked to restart your machine. 

NOTE:  Once you've restarted it MAY load properly. It MAY not. You might get the same "cannot start x" and offer you safe mode as what happened to me. If that happens try the steps below:

What I did : (i'm not sure that all these steps are required, But they worked for me while trying to get it going. You may try any combo of the steps below in a different order and have the same or different success.)

a. Chose safe mode when offered. (continue)
b. Selected >system>administration>restricted drivers> selected "NVIDIA"
c. Restarted computer. (it only offered safe mode again)
d. then selected >Applications>system tools>Envy
e. Selected "uninstall nvidia driver"
f. selected "install nvidia driver"
g. rebooted

WA-LA!!! it stuck and I have full Nvidia graphics with desktop effects!

If an update rolls out a new kernel, then you'll just need to start in safe mode and use envy - select "install nvidia driver" and apply. It will run through the install process, and ask for a reboot to bring back your full res desktop

I hope this helps. 


Now for the **Wireless:**
I finally got the wireless going on Ubuntu 7.10  on the HP - AMD Pavilion TK-57 Laptop (Model: dv6704nr),  or more commonly called a Pavilion dv6000. By default Ubuntu tried to use the Atheros restricted driver, but did not work. 

Open the terminal and type "lshw -C network" to see which wireless adapter hardware you have. My results were:

> 
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.


1.   Dowload the latest windows driver for the wireless card from here:[ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip)
(I know it says acer, but this is the driver for the AR5006EG chipset, if you have a different chipset you'll need to find the correct driver for it.)

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

### Post by jonnywombat on 2008-02-08
Thanks for a great how to.. very clear and precise and easy to understand.

I followed it for getting the wireless running on my HP G6065.. 

All has gone well, and the output on "ndiswrapper -l" is as per your post. I cut and pasted the rest of the instructions into terminal and then rebooted. However upon reboot I do not have wireless connectivity.

I reverted back to my trusty usb stick and that worked jusr fine.. any ideas where to go from here?

Thanks again

Jonny

---

### Post by nzruss on 2008-02-08
I'm guessing the windows driver for my laptop differs from yours. (which still loaded correctly into ndiswrapper, its just not the right one...)

What do you get when you type:

> lshw -C network

If it differs from mine, **(AR5006EG)** then All you need to do is do a search for your correct windows wireless driver for your particular chipset and use the   "  >system>administration>windows wireless driver  " tool to swap them out. You've already done all the rest of the hard work. 


Does that help?

---

### Post by jonnywombat on 2008-02-08
My output is

 >  
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

Also as it happens my machine did the forced disk check on booting.. Thus i had a text boot and not a graphical one. After loading kernel modules ndiswrapper tried to load the drivers but it reported "failed to load drivers" and threw what looked like an error code which I think may of been 338, but could easily of been different.

Thanks again 

Jonny

---

### Post by nzruss on 2008-02-09
So on a normal boot you get a graphical error with the ndis faultcode appearing? 

Did you blacklist the old wi-fi drivers? Double check the ndiswrapper has loaded the driver? 

Are you running 64bit????  (i'm running 32bit i386 ubuntu - as certain things are better supported on difficult hardware - and 64bit buys you more ram and floating point calcs which I have little need for..)

If you followed the steps, then i'm pretty stuck as to what it could be...  (i'm *not *very uber with Linux - just manage to keep my head above water).

---

### Post by Dittie on 2008-02-10
I found that if you use the 64bit install, you'll get errors. the 32 bit install worked great for me on my dv6704nr with the instructions above.

---

### Post by jonnywombat on 2008-02-10
I am using 64 bit ubuntu, I purposely hunted out a laptop with althlon 64 x2 so I could. I have used 64 bit since 7.04, and I have not really had many issues i could not solve on way or another.

Looks like this might be a 64bit issue.. I had followed all steps exactly, and blacklisted the restricted driver.

The error (code 358 ) is only visible when the machine checks the disk within the boot process, and not during a "normal" boot
The only other possibility I can think of is I use a usb stick and I wonder if this could cause a conflict.

Thanks for your help. I guess I will have to hope that there is native support for the atheros chipset in Hardy.

Jonny

---

### Post by jonnywombat on 2008-02-14
Gave up on 64 bit and switched to 32bit. Process worked flawlessly. Thanks...
Jonny

---

### Post by nzruss on 2008-02-14
Am glad you got it working!!! YAY!!!

---

### Post by nzruss on 2008-02-14
That recent update required me to re-install the nvidia drive with envy. 

It'll boot into safe mode, so continue, then login normally and chose > applications > system tools > envy

then select "install nvidia driver" and click apply. 

Say yes to the reconfigured xorg.conf, and yes to the reboot. 

--- back to normal.

---

### Post by jonnywombat on 2008-03-22
Hi all...

Have been playing with Hardy 64bit..and I used this technique to install my wireless drivers.. and apart from using 64bit xp driver rather than the one specified it worked just fine without any issue

Jonny

---

