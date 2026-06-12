---
title: "Ibm T22"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Merlinenfrance on 2006-07-12
Can anyone advise if Ubunto will work on an IBM T22 without problems.  Would like to know prior to installing.

Thanks

Merlin

---

### Post by geos2 on 2006-07-12
i don't think ubuntu "just works" on any machine at this point.

Out of the box, Ubuntu basically functions on my T22 with the exception of sleep and hibernate, but there are always little issues.

check out: [www.thinkwiki.org](www.thinkwiki.org) for lots of info...

---

### Post by weekend warrior on 2006-07-12
You should encounter very few (if any) major problems and perhaps a few annoyances and if you do there are plenty of us here with Thinkpads to help you. There's also much information on the net. Google is your friend, searching for "T22 Ubuntu" will give you plenty of results.

For what its worth, my trusty T23 has run all the major linux distros on it without complaint.

Also, Ubuntu allows you to try it as a live CD before installing to see if things work. Just put the CD in and reboot. You'll see.

Oh and remember it's Ubunt**u** ;)


Edit: You may want to consider trying Xubuntu on your T22, especially if it doesn't have much memory - [www.xubuntu.org](www.xubuntu.org)

---

### Post by tedrogers on 2006-08-07
I wish I could just install the Live CD and reboot.

My T22 hangs on the "mounting root filesystem" section of the live DVD bootup. The drive just gurgles and makes lost of noises that sound very bad!

I have had no other problems with the drive though. It works for everything else I have installed, and many other linux live DVD/CD distos including Slax, Gentoo, Suse, DSL and Knoppix.

The T22 has the Savage gfx chipset and I've heard this can cause problems....but basically I'm stumped.

Also I can't get kubuntu installed either.

Any ideas what's going on?

Thanks.

---

### Post by jruschme on 2006-08-07
Assuming that the T22 has the same quirks as the T20, the problem is the Sava graphics. You need to boot the LiveCD in "safe graphics" mode which uses the generic Vesa driver. You should then be able to install ubuntu normally.

Enabling the Savage driver takes a bit of editing of the xorg.conf file. Look at ThinkWiki ([http://www.thinkwiki.org](http://www.thinkwiki.org)) for details.

FYI, it is possible to get it working, even DRI (though you may be limited to 16-bit color).

John

---

### Post by tedrogers on 2006-08-08
Hi and thanks for your reply.

I tried booting from the Live DVD in Safe Mode but again the same problem, it just stalls at the 'mounting root filesystem' point and the drive churns away. It sounds like it's really doing some damage - a kind of really loud skipping sound.

Is there anything else I can try?

---

### Post by isharra on 2006-08-09
I had no such problems on this T22.  Try another disk. The dvd writer or your drive may be slightly misaligned. Safe graphics worked for me every time. F6 and adding "ec_intr=0" to the kernel options usually worked. (Brings you up with the savage driver instead of the vesa but since the savage driver does not always detect the card properly it's more chancy.)

---

### Post by jarviser on 2006-08-10
I had similar problems installing from CD-ROM onto T22 and onto 600x, however after around 3 or 4 attempts, each time getting a little further along the process, it installed and works really well (though I activated sleep mode in the /etc/default/acpi-support file, but had to take out the battery to wake it up again!).  I guess the Ubuntu disks are very tightly packed and elderly thinkpad drives can struggle to read them.

---

### Post by weekend warrior on 2006-08-10
tedrogers, try using the live CD versions as opposed to the DVD and make sure floppy=thinkpad is in your boot options. See if that helps.

---

### Post by The Road Below on 2006-08-11
Tried ubuntu and Suse on a t22 2648 and found xubuntu worked fine with a download/burned cd.  Savage definitely causes probs but xubunu did not exhibit these as ubuntu did.  Ubuntu would only boot every other time.  Seems like a common prob. I am an absolute Linux n00b.  Good luck!

---

### Post by isharra on 2006-08-11
For the T22 add the following lines to the device section for your savage card:
```
        VideoRam        8192
        Option          "DmaMode"               "None"
        Option          "BusType"               "PCI"
```

The savage driver assumes 16meg for video and dma transfers when agp. Unfortunately the savage chip installed only has 8meg and does not support dma transfers. 'man savage' for more information on options for the savage driver. That's a common problem for all xorg installations not just ubuntu.

If you're new to linux you might also want to take a look at [thinkwiki about the T22]("http://www.thinkwiki.org/wiki/Category:T22").

---

### Post by tedrogers on 2006-08-17
Alright...thanks....I will invetsigate.

But to do this I will have to install. First I need to get past these hanging problems.

Thanks for everyones advice so far. I will try a DVD burned slowly, I'll try the kernel options and if all of that fails I will try using the Live CD's instead (like I was advised it might just be the old style DVD ROM can't cope with the tightly packed DVD disk).

If I get any joy I'll be back...if not...I'll still be back! :)

Thanks again everyone.

-------------------------------------------------------------------

Ok, well I tried all the suggestions and using a Live CD instead of a DVD was the only one that would work. Plus I could only get this to work using Safe Mode.

I am not sure how I would add these lines into the device section for the Savage card:

        VideoRam        8192
        Option          "DmaMode"               "None"
        Option          "BusType"               "PCI"

Do I have to actually install Kubuntu to do this?

Thanks.


------------------------------------------------------------------

SUCCESS!

I found a post that suggested doing the following, and it worked perfectly. The only problem is my £ sign doesn't work on the laptop, but I think I messed up the keyboard type. Any ideas what this should be for an IBM T22, i.e. PC101, PC104, PC105 etc?

I didn't have to put the Option "DmaMode" "None" and Option "BusType" "PCI" into my xorg.conf file either, but although it worked for me without these it may not work for all.

Basically all I had to do was install using the text mode first and from then on it was plain sailing by following these instructions:

1. When the computer is booting up, enter the GRUB bootloader and select the "recovery" option.

2. After the system is fully loaded and you are presented with a command prompt as root, type "dpkg-reconfigure xserver-xorg" to enter the configuration utility.

3. Have the utility attempt to autodetect the card (for the T20, it should autodetect to the Savage driver).

4. Continue through the screens selecting the default values until you reach the screen telling you to "Enter the amount of memory (in kB) to be used by your video card." on the line, type "8192", because the T20 savage video card is an 8MB card... 8 x 1024kB. This is the critical step in getting the graphics to load correctly!

5. Continue selecting default values until you reach the screen where you must select "Easy" "Medium" "Advanced" or something regarding the way you will set the refresh rate. Select "Medium", and then on the next screen select "1024 x 768 @ 75 Hz"

6. For color depth, select "24".

7. Continue hitting "OK" through the wizard until you are dumped back to the command line. Type "telinit 6" to restart the computer. Let the computer boot completely, and you should see graphics!!!

I hope this helps others with T20 series laptops.

Now, my only other gripe is how to change the 'boot time' resolution from 640x480. It looks crappy! My 'booted' resoution is fine at 1024x768, but I would like the boot time resolution to be the same. Anyone know how to do this...in newbie speak please!

Thanks.

-----------------------------------------------------------------

Just to confirm that on a fresh install you don't need to do any of the above.....although the above still works ok.

Just log into the rescue mode by pressing escape when promted for the menu - this logs you in as root.

Then go to the directory where xorg.conf is located. I type "cd /etc/X11" at the prompt.

Then edit xorg.conf using vi. I type "vi -n xorg.conf", use the cursors to get about, the insert key to make changes, escape to get out of insert mode, and ":x" to quit and save. (Took me ages to learn how to save!)

In the device section, as stated above, enter these values:

Option		"BusType" "PCI"
Option		"DmaMode" "None"
VideoRam	8192            

**NOTE: You don't need to specify 24 bits for the default depth ***

Remember, the Escape key gets you out of editing mode and you save using ":x"!

Reboot the system using "shutdown -r now".

It should all work fine and boot into Gnome perfectly.

I hope this saves someone a lot of time. :wink:

---

### Post by wykedengel on 2006-09-18
this helped for me first and i hope it works for you. i downloaded and install breezy ubuntu without any problems. from there i did the following:

inserted 6.06
rebooted pc
changed vga mode to 640x400 and
selected "install in safe graphics mode"

it loaded up with no problems and i clicked the install button. yeah, it takes a little longer and eats up a second cd, but i think it is well worth it!

good luck to everyone!

---

### Post by tedrogers on 2006-11-11
Really it's quite simple now....once you have installed via text mode install (maybe alternate CD).

On a fresh install:


1. Boot into Rescue mode (press ESC when you see GRUB menu)
2. At the prompt type sudo pico /etc/X11/xorg.conf

Add into the Section Device area (look for Savage S3 and this will be it):

Option "BusType" "PCI"
Option "DmaMode" "None"
VideoRam 8192 

The whole thins looks like this:

Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "BusType"       "PCI"
        Option          "DmaMode"       "None"
        VideoRam        8192
EndSection

3. Save and reboot.

This should at least get you into X windows.

Hope this helps.

---

### Post by opossumjack on 2006-11-25
Hi, I've just installed the new version of ubuntu (6.10) on my thinkpad T22.

I have a little problem...](*,) 

If I leave the computer alone for a while, without touching anything, ubuntu hang on and I can't unfreeze it...

can anyone help me?!?!?

thanks

OpossumJack

---

### Post by tedrogers on 2006-11-25
Try your Power Management in System > Prefernces....put everything you can onto Never or Off or the nearest equivalent.

Then see what happens...if the problem has gone then it was a Power Management thing.

I currently have an ACPI problem with my T22, which I am trying to fix....maybe the two are related.

If I find another solution I will let you know....but until then you might want to try this, which will disable ACPI on your system (also allowing you to have the option to use ACPI if you still want to by choosing the appropriate boot option):

In a terminal type:

```
gksudo gedit /boot/grub/menu.lst
```

Now COPY your Ubuntu stanzas

In the copied stanzas, change the title to "Ubuntu No ACPI"

At the end of the "kernel (hd0,x)/vmlinuz root=/dev/hdxy vga=791"

Add pci=noacpi to the end of the line, like this:

```
kernel (hd0,x)/vmlinuz root=/dev/hdxy vga=791 pci=noacpi
```

Reboot

Now you will see a grub entry for Ubutnu No ACPI; Boot it.

If you have problems, you can always return to your previous Ubuntu boot and re-post...

---

### Post by po0f on 2006-11-26
To anyone interested, this is my T22's xorg.conf Device section on Debian (not going to put Ubuntu on it, but this should still work under Ubuntu as well):
```
[FONT="Courier New"]Section "Device"
    Identifier "Videocard0"
    Driver "savage"
    Option "BusType"    "AGP"
    Option "DmaType"    "AGP"
    Option "DmaMode"    "None"
    Option "AGPMode"    "2"
    Option "AGPSize"    "16"
    Option "SWCursor"   "true"
    #VideoRam 8192
EndSection[/FONT]
```

DRI is working, glxgears ~390 (~130 without).

---

### Post by opossumjack on 2006-11-26
Thanks a lot Tedrogers. I tryed it.... now I'm gonna see what happens...:rolleyes: 

I've also noticed the hard disk stops spinning just a moment before ubuntu freezes.... any ideas?:-# 

thanks in advance
opossumjack

---

### Post by tedrogers on 2006-11-26
> **opossumjack said:**
> Thanks a lot Tedrogers. I tryed it.... now I'm gonna see what happens...:rolleyes: 

I've also noticed the hard disk stops spinning just a moment before ubuntu freezes.... any ideas?:-# 

thanks in advance
opossumjack

Which bit did you try....disabling ACPI or turning off Power Management options?

The hard disk thing sounds like an ACPI issue to me.

---

### Post by opossumjack on 2006-11-28
I left the laptop inactive for a whole afternoon....and in the evening it still worked

but when I activate the internet connnection (via ethernet) it freezes.....](*,) 

I don't know what to do......I'm desperate...:( 

Opossumjack

---

### Post by tedrogers on 2006-11-28
Is this without disabling the ACPI and/or the Power Management? Tell me exactly what is going on here and I may be able to help.

Does your computer stop working when you plug the ethernet cable in without disabling the ACPI/Power Management? So, without you doing anything to the machine?

Or does it stop working when you put the ethernet cable in AFTER you have disabled the ACPI and/or power management?

The more detail you can give me the better chance I will have of helping you.

Thanks.

---

### Post by wieman01 on 2006-11-28
Seems to me that Ted is on the right track... But frankly this looks like a hardware problem in my opinion. When the computer freezes, can you still open another terminal session by pressing:
> CRTL + ALT + F1
Then enter you username & password. If this works, then simply X has crashed. 

Putting ACPI aside, have you tried Ubuntu Dapper (6.06) before? Perhaps it makes more sense for you since your T22 is a fairly outdate model. Ubuntu Dapper comes with long-term support & is less experimental than Edgy. Just a thought, perhaps this resolves all your problems.

---

### Post by opossumjack on 2006-12-02
I'm gonna install dapper right now, because I need the laptop working... 

I hope this one will work...:rolleyes: 

TO TED:
I have disabled ACPI and all the options in gnome power management before plug the ethernet....but it freezes....](*,) 


Thanks to everybody

OpossumJack

---

### Post by tedrogers on 2006-12-02
Dapper is behaving well for me so far...just switched back too...although it is a LOT slower! :(

Nevermind...as long as it all works.

---

### Post by wieman01 on 2006-12-02
Hi Ted, 

What do you mean by "a lot slower"? Boot? That's no surprise because the boot logic has changed in Edgy.

---

### Post by tedrogers on 2006-12-02
Just general running speed, i.e. how long it takes to fire applications, how long synaptic takes to load, alacarte menu editor takes forever...and anyway...I still have the same Alsa problems and so I'm going back to fresh Edgy install. 

I had the mic/audio recording/skype working when I first installed edgy...I think automatix2 is messing it all up as I noticed it installed some alsa-base or something.

Today has been a long day of installing and reinstalling over and over so far!

Hopefully I can get to the bottom of this.

---

### Post by opossumjack on 2006-12-02
:cry: :cry: :cry:


I went down to a new 5.10 install.... but....](*,) 

It freezes down.............:( 

I didn't format the home partition... may this create problems?
Should I format this partition too?

Maybe I will try with kubuntu..........:-? 

OpossumJack

---

### Post by tedrogers on 2006-12-02
You almost certainly want to format your root (/) and your swap (/swap)....any other partitions you can leave intact and if you want to you can mount them during the install.

For example, I have:

hda1 as / (root)
hda5 as /swap
hda3 as /mount/hda3

This means that it boots from hda1 and this is where all my install files are kept, inc. my /home directory. hda5 is my swap space and hda3 is another partition which is mounted to the /mount/hda3 directory. I can get to my hda3 partition by browsing Computer > File System > Mount. In the mount directory I will find hda3.

Hope this helps.

Oh...and I still have the same problem with my sound capture/mic. Looks like I'm screwed on this front. I've tried dapper and edgy now. It's bugging me out!

---

### Post by opossumjack on 2006-12-02
I don't wanna install WINDOWS.....](*,)

---

### Post by tedrogers on 2006-12-02
If all else fails...maybe try the new Fedora Core 6...it's quite cool!

---

### Post by wieman01 on 2006-12-02
> **tedrogers said:**
> Just general running speed, i.e. how long it takes to fire applications, how long synaptic takes to load, alacarte menu editor takes forever...and anyway...I still have the same Alsa problems and so I'm going back to fresh Edgy install. 

I had the mic/audio recording/skype working when I first installed edgy...I think automatix2 is messing it all up as I noticed it installed some alsa-base or something.

Today has been a long day of installing and reinstalling over and over so far!

Hopefully I can get to the bottom of this.
Then something else is odd, I doubt it has much to do with Dapper. Nonetheless if the mic is still an issue, then back to Edgy you go. Are you sure, this is not a hardware issue? Have you checked out the same laptop & mircrophone using Windows? And played around with Alsamixer? Mmm...

---

### Post by tedrogers on 2006-12-03
Yesterday I took the laptop apart to see if the mic was still connected...and it was. It throughputs sound to the main speakers, so much so that I get feedback if the volume is high enough...so it would appear that the hardware is working.

My next step is to try some other OS, maybe slax live or demudi (a specialist music variation of debian) [http://demudi.agnula.org/](http://demudi.agnula.org/)

I would rather try something live first than having to reinstall a windows image..plus this would destroy all of my ext3 partitions. I may consider a fresh install of XP/2k on just one partition....but I guess I would have to format it to fat32 first. 

As per the speed thing...having experienced dapper and edgy in the same day...I can confirm that edgy is much faster in all respects than dapper on my old IBM T22 800mhz machine.

---

### Post by tedrogers on 2006-12-03
Well..I can now confirm that the mic is working fine.

I tried several live CD's (inc. Slax, Knoppix, Demudi and DSL) and all of these exibited the same problems with my mic.

Then I reinstalled win2k (!!) and the mic worked fine...I recorded my voice and played it back!

So after many hours of reinstalling and getting lots of MBR and grub problems after installing win2k, I'm now back on edgy but still with the same issues.

It has to be a linux thing now. Maybe there is some driver out there that I need?!?

---

### Post by wieman01 on 2006-12-03
Are you sure Linux has recognized your card correctly? This is a bit strange, one of the Linux distribution should definitely have worked... If all of them yield in the same problem... Well, strange.

Perhaps the volume is still set to ZERO by default after installing Linux? Do you have a hardware switch on the T22? That could be it after all...

---

### Post by tedrogers on 2006-12-04
> **wieman01 said:**
> Are you sure Linux has recognized your card correctly? This is a bit strange, one of the Linux distribution should definitely have worked... If all of them yield in the same problem... Well, strange.

Perhaps the volume is still set to ZERO by default after installing Linux? Do you have a hardware switch on the T22? That could be it after all...

I'm pretty convinced the linux distros are all recognising my cirrus logic on-board sound card.

I'm not entirely sure I know what you mean by hardware switch, if you mean a physical switch / jumper for the mic, then no it doesn't.

Nothing really explains why it should work in Windows 2000 and not any of the linux distros though!?! ](*,) 

I have posted a bug report on launchpad, so maybe that will yield some results.

But if anyone else out there has a T20, T21, T22 or T23 maybe they could test this out for me?

Thanks.

---

