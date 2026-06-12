---
title: "Problems with 10.04 and Toshiba A505 S6005"
date: 2010-05-03
forum: Hardware
---

### Post by gitboxgreg on 2010-05-03
I recently installed 10.04 on my laptop and was having trouble getting wireless and my usb working. I followed this tutorial to get those issues fixed [http://ubuntuforums.org/showpost.php?p=9009017&postcount=26]("http://ubuntuforums.org/showpost.php?p=9009017&postcount=26") but now I am having a few more problems. 

The main one is that ubuntu doesnt recognize the battery in my laptop. The power manager only shows options for on AC power and I have no way of telling how much battery I have. There is no applet in the panel and nothing happens when I unplug the power. 

The other problem I have is that I can not turn the trackpad on and off. It will just remember if it was on in windows and be on in ubuntu or if it was off it will stay off in ubuntu.

If anyone has any insight into this problem it would be greatly appreciated!

---

### Post by gitboxgreg on 2010-05-03
bump

---

### Post by gitboxgreg on 2010-05-04
anyone else have this problem?

---

### Post by gitboxgreg on 2010-05-04
bump, please help!

---

### Post by gitboxgreg on 2010-05-07
so no one else has this laptop?

---

### Post by nirvale on 2010-05-07
hallo, I have de same laptop, and many problems of course, i tried to install ubuntu studio 10.04, 9.10 and always became a disaster, in buntu studio 10.04 after a hard work to install, never come the first run of the OS, always black screen. NObody have the solution, the toshiba's laptops not working with any GNU/Linux.

toshiba dont't want to program modules for GNU/linux (maybe becasu MS is a toshiba's partner)

And UBUNTU, FEDORA, CENTOS... don't want to program modules for toshiba... why?

And if you get linux running on your toshiba, then the acpi doesn't work, and your laptop becomes so warm becuse the sensors and fan ire unfunctional under GNU/linux OS, it is so dangerous for the processor.

Dmt!!!

good look with the wintendo.... windows
:guitar:):P:lolflag:

---

### Post by bcericksen on 2010-05-08
> **gitboxgreg said:**
> so no one else has this laptop?

I have a Toshiba A505.  I installed Ubuntu 9.10 (Karmic Koala).  It has the following behavior:

- No USB device is recognized: mouse, keyboard, USB drives, and wi-fi modem are all nonfunctional.  
- The mousepad does not turn on or off.  If it was on in Windows it stays on after reboot into Linux; if off it stays off.  If on the mousepad and buttons work normally.
- The file system _can_ see Windows files through the /host directory tree.  I have another computer where this is not the case, so I'm counting blessings here.

My workarounds are to use the internet and devices in Windows, then access downloaded files through the /host directory if I need them in Linux.  Far from ideal. 

I learned that Toshiba does not support Linux at all from the Toshiba forum, [http://laptopforums.toshiba.com/t5/Drivers-and-Utilities/A505-s6033-why-it-doesn-t-have-a-windows-7-32-bit-display/m-p/93125#M6454](http://laptopforums.toshiba.com/t5/Drivers-and-Utilities/A505-s6033-why-it-doesn-t-have-a-windows-7-32-bit-display/m-p/93125#M6454)

How does one access USB devices when there are no specific drivers?

Bryan

---

### Post by foolusion on 2010-05-09
I have this laptop too. I can boot it with "acpi=noirq". I tried recompiling the DSDT with iasl and there were no errors. So i guess the problem is different from the solution in this thread [http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)

---

### Post by theviking10 on 2010-05-11
I have a Toshiba A505-s6005, and I can't even boot Linux. Live Discs will not run, and if I use a text installer then it will install on the hard drive, then fail to boot again. I have tried the most recent Ubuntu, and even the Fedora 13 Beta (final version out the 18th) which uses the most current kernel.


I believe I'll have to wait until the next round of distros to install a working Linux system - I believe Madriva or Gentoo will be updating soon. Also, openSUSE.

---

### Post by VE. on 2010-05-15
I am having these problems, too. 
Does ANYONE have any ideas?

---

### Post by kenaih on 2010-05-17
Hey guys, I just bought this Toshiba model and got the same problems you all have.

After some research, I think I've finally gotten all the issues solved.

My wireless card, the power manager showing the batteries, the usb problems, fan speed, multicore support, webcam, etc :)
In other words:** Full ACPI Support**

Here is the proof: [http://i39.tinypic.com/30vc19l.jpg](http://i39.tinypic.com/30vc19l.jpg)
You can see working the temperature monitor applet, the wireless card (without having to install the drivers), the batteries info, etc... 


This is what I did:

The main problem with this laptop is that the BIOS is buggy, and make some funny stuff with the DSDT tables.

There is already a patch with a solution for this problem (since March) but hasn't been included in the official kernel yet, so we have to compile our own kernel. 

We are going to use the Ubuntu sources for this, so first of all, install all the dependencies:

```
sudo apt-get install build-essential libncurses5-dev libncurses5 kernel-package
```


Then you need to get the kernel sources with the Ubuntu patches:

```
sudo apt-get install linux-source-2.6.32 
```

This is the 2.6.32-21-generic source code, which is based on the official 2.6.32-11 version from kernel.org.

So when you compile, you will get the "-11" prefix, don't worry about that.

Now we patch the source and configure it:
(notice the patch we are going to use is different from this one: [http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)
We are using a more updated patch from the kernel developers )

```

cd /usr/src
sudo tar xvfj linux-source-2.6.32.tar.bz2
cd linux-source-2.6.32
sudo wget 'https://bugzilla.kernel.org/attachment.cgi?id=25669' -O copydsdt.patch
sudo patch -p1 < copydsdt.patch
sudo cp /boot/config-2.6.32-21-generic ./.config
sudo make menuconfig

``` 

Now you will get a menu...

Select "Load an alternate configuration file"
ENTER
EXIT

(go to: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)    for a more explanatory tutorial regarding this)

Now we compile:

```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-a505 kernel_image kernel_headers

```
If you get permission problems, just execute "sudo su" before the 2 previous commands.
That will take like an hour.
After that, we will have 2 .deb files in /usr/src, we now install them :)
```

cd /usr/src
sudo dpkg -i linux-headers-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_i386.deb
sudo dpkg -i linux-image-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_i386.deb

```

Now we create an initrd file and copy the file to /boot

```

cd /usr/src/linux-source-2.6.32
sudo su
mkinitramfs-kpkg -o initrd.img-2.6.32.11+drm33.2-a505 2.6.32.11+drm33.2-a505
cp initrd.img-2.6.32.11+drm33.2-a505 /boot
exit

```

And we edit /boot/grub/grub.cfg , adding the following **bolded text**:
(you can use **sudo gedit /boot/grub/grub.cfg**, or your favorite text editor)

```

menuentry 'Ubuntu, with Linux 2.6.32.11+drm33.2-a505' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set a0fd8215-05f4-4c17-a7af-0d59f88e99b7
        linux   /boot/vmlinuz-2.6.32.11+drm33.2-a505 root=/dev/sda5 ro   quiet splash **acpi=copy_dsdt**
     **   initrd /boot/initrd.img-2.6.32.11+drm33.2-a505**
}
menuentry 'Ubuntu, with Linux 2.6.32.11+drm33.2-a505 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set a0fd8215-05f4-4c17-a7af-0d59f88e99b7 
        echo    'Loading Linux 2.6.32.11+drm33.2-a505 ...'
        linux   /boot/vmlinuz-2.6.32.11+drm33.2-a505 root=/dev/sda5 ro single 
        echo    'Loading initial ramdisk ...'
**        initrd /boot/initrd.img-2.6.32.11+drm33.2-a505**
}


```

**OPTIONAL**
That will be enough to get everything working, but the update-manager tends to modify the grub.cfg each time it gets kernel updates or other things... so, we are going to modify one more file, just not to have to modify the grub.cfg each time.

We edit the default grub config:

```

sudo gedit /etc/default/grub

```

And again, we add the **bolded text**...

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**acpi=copy_dsdt**"

```

Then we update the GRUB Menu
```

sudo update-grub

```

This will reconstruct the grub.cfg with the acpi=copy_dsdt option, but it will add it for all your kernels, including the original one.
Well, it's not like we are going to use other versions without that option anyway, so...

Now just reboot the machine and select the new kernel entry from your Grub Boot Menu.

That's it guys, now your Toshiba a505-s6005 will be 100% functional under Linux :)


By the way, if you want to get the temperature monitor, you need to install sensors-applet, hddtemp and acpi-support.
And to test the webcam, just install a program like cheese (sudo apt-get install cheese)

P.S.- If you can't even install the distro (black screen or something), that means you have an older version of Ubuntu 10.04 (probably a BETA or a RC version). 
The graphics chip from this laptop model  is an intel HD Graphics, and it's supported for Linux since 2.6.33 versions... the Ubuntu Team patched their 2.6.32 version for it to have the drivers working in the FINAL VERSION. So even if you have the latest RC version, it won't work... you need the final release.

---

### Post by gitboxgreg on 2010-05-18
Hm I get as far as here```
mkinitramfs-kpkg -o initrd.img-2.6.32.11+drm33.2-a505 2.6.32.11+drm33.2-a505

``` but then i get this error ```
Cannot find /lib/modules/2.6.32.11+drm33.2-a505

``` any idea what im doing wrong?

---

### Post by abd'allah on 2010-05-18
I also have a Toshiba A505 S6005. I am trying to install Ubuntu 9.10 from the "Ubuntu 9.10 Desktop Edition" CD. I have used the same CD to install it on my PC and I have been using it successfully for the last few months.
 
But, unfortunately I am having severe troubles installing it on the Toshiba laptop. Problems: 
- wubi.exe does not run
- Boots from the CD and the installation procedure stops after selecting the language. Laptop hangs with a black screen.
- Tried the following but none of them works (same black screen appears) : 
   * Ubuntu 9.10 Demo
   * Test for Memory
   * And all the other options that appear on that setup menu
 
Did anyone have this problem before? Please help me out.

---

### Post by kenaih on 2010-05-18
> **gitboxgreg said:**
> Hm I get as far as here```
mkinitramfs-kpkg -o initrd.img-2.6.32.11+drm33.2-a505 2.6.32.11+drm33.2-a505

``` but then i get this error ```
Cannot find /lib/modules/2.6.32.11+drm33.2-a505

``` any idea what im doing wrong?


You are not doing anything wrong, I forgot a crucial step (installing the compiled kernel before creating the initrd image)
Also, I've changed this line:

```
fakeroot make-kpkg --initrd --append-to-version=-**a505** kernel_image kernel_headers
```

Go back to my previous post, the manual should be fine now.

> **abd'allah said:**
> I also have a Toshiba A505 S6005. I am trying to install Ubuntu 9.10 from the "Ubuntu 9.10 Desktop Edition" CD. I have used the same CD to install it on my PC and I have been using it successfully for the last few months.
 
But, unfortunately I am having severe troubles installing it on the Toshiba laptop. Problems: 
- wubi.exe does not run
- Boots from the CD and the installation procedure stops after selecting the language. Laptop hangs with a black screen.
- Tried the following but none of them works (same black screen appears) : 
   * Ubuntu 9.10 Demo
   * Test for Memory
   * And all the other options that appear on that setup menu
 
Did anyone have this problem before? Please help me out.

You won't be able to get this toshiba model fully working with Ubuntu 9.10.
The reason is that the i3-330m processor and the intel HD chip are both too new for Ubuntu Karmic.
You can install it, though...  with the ACPI=off option, and then compile a more updated kernel version, but it will be harder than with Ubuntu 10.04

---

### Post by gitboxgreg on 2010-05-19
you sir are awesome! I finally have ubuntu working on my laptop! There was just one thing for this part ```
sudo cp /boot/config-2.6.32-21-generic .config
``` I had to run it as ```
sudo cp /boot/config-2.6.32-21-generic ./.config
``` but other than that this guide is flawless! 

I seriously can not thank you enough. Here is m proof it is working [http://imgur.com/j749y.jpg]("http://imgur.com/j749y.jpg")

I am going to slap a solved tag on this thread.:)

---

### Post by kenaih on 2010-05-19
> **gitboxgreg said:**
> you sir are awesome! I finally have ubuntu working on my laptop! There was just one thing for this part ```
sudo cp /boot/config-2.6.32-21-generic .config
``` I had to run it as ```
sudo cp /boot/config-2.6.32-21-generic ./.config
``` but other than that this guide is flawless! 

I seriously can not thank you enough. Here is m proof it is working [http://imgur.com/j749y.jpg]("http://imgur.com/j749y.jpg")

I am going to slap a solved tag on this thread.:)

Thanks for the corrections. I've updated the guide for the future owners of this model.

Glad you get it working. I spent hours trying to get my laptop running Ubuntu, since there was no specific guide... it was a hell!!.
I'm happy I could help other Toshiba505 owners so they don't suffer too much with all this :)

---

### Post by purelinuxuser on 2010-05-19
Awesome, this guide worked PERFECTLY for me too! :guitar:

This should really be added to the "Tutorials and Tips" section as a HOWTO, as this Toshiba is BY FAR the most Linux-unfriendly laptop I've ever seen.

---

### Post by Lord Arctic on 2010-05-27
New User, and love this guide, but after doing a clean install of Ubuntu on my a505-s6005 I have run into few discrepancies: 
 
sudo cp /boot/config-2.6.32-22-generic-pae ./.config 
was what I had to use to get to the point of compiling. Not sure what else has changed and im not sure if I am doing something wrong, or missed a step, will let you know once I get to the installing part.....
 
Ok Installed Great..No Problems that I can see
 
Now is there a way to make an Installation CD with this patch added??

---

### Post by galley3175 on 2010-05-27
This fixed my Toshiba E-205 S1904.  I had worked through the other thread listed in this post, but this really worked for me.  Everything is working.  Startup and Shutdown function keys, and battery icon.

WOO HOO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Galley3175

---

### Post by rampage355 on 2010-06-06
I have this same problem on my A505 S6020 but I can even get 10.4 to boot after install just get the black screen, it blacks out right before the grub menu. how can I get past that to compile the new kernal?

---

### Post by purelinuxuser on 2010-06-06
> **rampage355 said:**
> I have this same problem on my A505 S6020 but I can even get 10.4 to boot after install just get the black screen, it blacks out right before the grub menu. how can I get past that to compile the new kernal?

Hold down shift as you boot up the system, and that should bring up the GRUB menu.  Highlight the top option, press "e" to edit the kernel options, and add "nomodeset" at the end.  It won't be pretty when Ubuntu boots up, but it should work.

If anybody doesn't mind, I'm going to post a HOWTO on this in the Tutorials & Tips forum.  Also, there is no need to recompile the kernel- you can use the kernel 2.6.35 packages at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/").  Then just add the "copy_dsdt" option like described above.

---

### Post by markos7007 on 2010-06-06
im having a problem. i have the same laptop but i cant even install ubuntu(using a usb not cd). im able to click install ubuntu to hard disk then it does that ubuntu load screen, then it gives my a couple errors in a black screen. One of them is "unable to find medium containing live file system".  if you want me to list all of the errors i will.

---

### Post by markos7007 on 2010-06-06
ok i think it could be a usb problem or something because the wubi install works. is there something imdoing wrong because id rather install ubuntu on another partition then part of my windows 7.

---

### Post by rampage355 on 2010-06-07
purelinuxuser are you saying that the new kernal has all the fixes in it?

---

### Post by rampage355 on 2010-06-07
ok, I installed the new kernel that you gave us the link to and added the dsdt line. It appears that everything is working except for the and wireless network, any suggestions?

---

### Post by rampage355 on 2010-06-07
I installed the updates here is what i noticed that does not work properly
[LIST]
[*]Web Camera (very very slow)
[*]Wireless 
[/LIST]

Here is what is working from before
[LIST]
[*]Battery Management
[*]Video
[/LIST]

I tried to install the 2.6.35-020635rc1 and got "Error: Dependency is not satisfiable: linux-headers-2.6.35-020635rc1"

And I got restricted drivers pop-up for Nvidia should i install it or should I install the drivers I have NVIDIA-Linux-x86_64-195.36.15?

---

### Post by markos7007 on 2010-06-08
purelinuxuser can u notify me when the howto post is up because im lost on the other guide and would like to get this running somewhat correctly on my pc

---

### Post by rampage355 on 2010-06-08
well i followed the directions to compile and i have to say it is awesome to have a fully functioning laptop, with the kernel that was mentioned I had some video issues so that made me decide to compile. kenaih do you happen to have the link to the bug on [http://bugzilla.kernel.org](http://bugzilla.kernel.org) I looked a little and could not find it. I would like to watch it so I can go to that new kernel when it is released.

Thanks everyone for all the hard work that was put into making this work. I will be complaining to Toshiba not that it will help much.

---

### Post by rampage355 on 2010-06-09
since i have compiled the kernel the only issue that i have has is with my wireless r8192. Transferring large amounts of data from the laptop to my server will cause my laptop to lock up solid. It does not do it with the wireless turned off and running on wired. Anyone experience this?

---

### Post by rampage355 on 2010-06-09
Well there is new drivers as of yesterday for the 8192 but they don't seem to want to install with the custom kernel, I am probably just doing something wrong. Can anyone help? Thanks

---

### Post by rampage355 on 2010-06-09
sorry here is the error i get if this helps

greg@my-desktop:~/Downloads/New Laptop Drivers/rtl8192se_linux_2.6.0017.0507.2010$ make
make[1]: Entering directory `/usr/src/linux-source-2.6.32'
make[1]: *** No rule to make target `Laptop'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [all] Error 2
greg@my-desktop:~/Downloads/New Laptop Drivers/rtl8192se_linux_2.6.0017.0507.2010$

---

### Post by cerati88 on 2010-06-10
This was perfect. Thank you so much. I confess that I do a lot on Windows. But I do need the quiet and perfect and calm of Ubuntu.

---

### Post by Adderoll on 2010-06-10
Hello!  This is my first time doing anything like this...and im getting stuck.

What I have:  Toshiba L505D-LS5007  AMD M500 HDRadeon 4100

I currently have 10.04 installed with the 2.6.32 Kernel and wanted to try and compile this kernel for giggles as this would be my first time to do so.  The only things that are not working on my laptop at the moment are the battery monitoring function, and CPU throttling.

The part that I am getting stuck on is the statement: 
wget 'https://bugzilla.kernel.org/attachment.cgi?id=25669' -O copydsdt.patch

When I try to execute this command I am met with the following:
--2010-06-10 20:38:21--  [https://bugzilla.kernel.org/attachment.cgi?id=25669](https://bugzilla.kernel.org/attachment.cgi?id=25669)
Resolving bugzilla.kernel.org... failed: Name or service not known.
wget: unable to resolve host address `bugzilla.kernel.org'
root@Toshtop:/usr/src/linux-source-2.6.32#

Am I doing something wrong?  Sorry if this is really simple but I am trying to learn!

Many thanks in advance!

---

### Post by Adderoll on 2010-06-11
Nevermind i got it!

---

### Post by donpuri on 2010-06-11
> **rampage355 said:**
> since i have compiled the kernel the only issue that i have has is with my wireless r8192. Transferring large amounts of data from the laptop to my server will cause my laptop to lock up solid. It does not do it with the wireless turned off and running on wired. Anyone experience this?

I used to have the same problem, just download drivers from:

**[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)**

(I use the 8192se driver, but my Laptop is a A505-s6033, which is exactly the same that the A505-6005, except for the processor) then unpack, move to the directory you unpacked the files and type:

> 
sudo make clean
sudo -s
make
make install
modprobe r8192se_pciReboot your machine and Voila! your wireless is fully functional.

By the way: Any luck with the webcam? mine is working really sloooooooow...

  Oh! My apologizes, my English is really crappy... XD

---

### Post by Adderoll on 2010-06-11
BINGO!

Can't thank you enough for this write-up!  Happy to report that everything is working like a charm on my laptop now.  I still don't think the CPU throttling is operating but can't really tell.  Anyone have a useful tool for monitoring this?  I know on the windows platform i use CPU-z.  CPU-z will actually show my processor revving up and down as it is being used.  

Anyway,  Thanks for the write-up!  Very easy to use.:p

---

### Post by kenaih on 2010-06-12
> **Adderoll said:**
> BINGO!

Can't thank you enough for this write-up!  Happy to report that everything is working like a charm on my laptop now.  I still don't think the CPU throttling is operating but can't really tell.  Anyone have a useful tool for monitoring this?  I know on the windows platform i use CPU-z.  CPU-z will actually show my processor revving up and down as it is being used.  

Anyway,  Thanks for the write-up!  Very easy to use.:p


Just type the next command:

```
cat /proc/cpuinfo  | grep MHz 
```

And change it to:

```
cat /proc/cpuinfo  | grep model 
```

to see your cpu model.

For example, the output on my laptop is:

model name	: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
for the second command, and:

cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000
cpu MHz		: 933.000

for the first one in normal conditions... (which means just firefox,gedit and rhythmbox :))

That frequency is less than half the full cpu performance, so yeah, cpu throttling is working, at least for me :)


EDIT:
I just found out there is a "CPU Frequency Scaling Monitor" applet already installed on Ubuntu Lucid, so just add that applet on your top panel (you know, right click-> Add to Panel -> CPU Freq.... )

---

### Post by Adderoll on 2010-06-12
Sweet!

Thanks for the info on that.  That CPU frequency monitor also allows you to change the power settings on each processor core as well.  That is just awesome.  I think I'm going to try this Linux thing out a little longer.

---

### Post by kenaih on 2010-06-12
> **rampage355 said:**
> sorry here is the error i get if this helps

greg@my-desktop:~/Downloads/New Laptop Drivers/rtl8192se_linux_2.6.0017.0507.2010$ make
make[1]: Entering directory `/usr/src/linux-source-2.6.32'
make[1]: *** No rule to make target `Laptop'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [all] Error 2
greg@my-desktop:~/Downloads/New Laptop Drivers/rtl8192se_linux_2.6.0017.0507.2010$

Hi Rampage,

I think the problem is simply that you are using "spaces" on your directory ("New Laptop Drivers"). Change it to "New-Laptop-Drivers" or something like that.

Also, don't forget to disable the current module when you install the new driver (sudo rmmod r8192se_pci)

---

### Post by careertargetph on 2010-06-13
I encountered similar problem.. Anyone here can provide me a step-by-step procedure in solving this matter.

---

### Post by kmullins on 2010-06-17
Thank you very much. This guide worked perfectly on my L505D-GS6000 laptop. The only minor change I had to make was I somehow ended up with kernel version x.x.x-15 instead of x.x.x-11.

---

### Post by DillyT33 on 2010-06-23
I followed the guide step by step. The only thing i am having trouble with is the battery icon is not coming up at the top? I tried "Adding to panel" and then looking for power management but couldn't find it.

---

### Post by Lord Arctic on 2010-06-30
WARNING ::::
 
DO NOT Upgrade the Bios to 1.30 Version from the Toshiba Website, it messes up the BIOS by fixing things, 
 
IF you did not follow this advice and try to install Ubuntu (any flavor Kubuntu, Xubunto included) you get a ton of ACPI errors and a lockup with installing.
 
FIX :  Windows will not allow you to install an older version of the BIOS from within windows, BUT you can make a BIOS install CD and it WILL allow you to go back to the older (and working in Ubuntu) 1.20 version
 
[http://cdgenp01.csd.toshiba.com/content/support/downloads/sat6v120.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/sat6v120.exe)
 
is the location of the Older 1.20 Bios download, Im not sure how long that will last but it is Official Toshiba Site

---

### Post by kecek on 2010-07-04
> **kenaih said:**
> Hey guys, I just bought this Toshiba model and got the same problems you all have.

After some research, I think I've finally gotten all the issues solved.

My wireless card, the power manager showing the batteries, the usb problems, fan speed, multicore support, webcam, etc :)
In other words:** Full ACPI Support**

Here is the proof: [http://i39.tinypic.com/30vc19l.jpg](http://i39.tinypic.com/30vc19l.jpg)
You can see working the temperature monitor applet, the wireless card (without having to install the drivers), the batteries info, etc... 


This is what I did:

The main problem with this laptop is that the BIOS is buggy, and make some funny stuff with the DSDT tables.

There is already a patch with a solution for this problem (since March) but hasn't been included in the official kernel yet, so we have to compile our own kernel. 

We are going to use the Ubuntu sources for this, so first of all, install all the dependencies:

```
sudo apt-get install build-essential libncurses5-dev libncurses5 kernel-package
```
Then you need to get the kernel sources with the Ubuntu patches:

```
sudo apt-get install linux-source-2.6.32 
```This is the 2.6.32-21-generic source code, which is based on the official 2.6.32-11 version from kernel.org.

So when you compile, you will get the "-11" prefix, don't worry about that.

Now we patch the source and configure it:
(notice the patch we are going to use is different from this one: [http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)
We are using a more updated patch from the kernel developers )

```

cd /usr/src
sudo tar xvfj linux-source-2.6.32.tar.bz2
cd linux-source-2.6.32
sudo wget 'https://bugzilla.kernel.org/attachment.cgi?id=25669' -O copydsdt.patch
sudo patch -p1 < copydsdt.patch
sudo cp /boot/config-2.6.32-21-generic ./.config
sudo make menuconfig

```Now you will get a menu...

Select "Load an alternate configuration file"
ENTER
EXIT

(go to: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)    for a more explanatory tutorial regarding this)

Now we compile:

```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-a505 kernel_image kernel_headers

```If you get permission problems, just execute "sudo su" before the 2 previous commands.
That will take like an hour.
After that, we will have 2 .deb files in /usr/src, we now install them :)
```

cd /usr/src
sudo dpkg -i linux-headers-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_i386.deb
sudo dpkg -i linux-image-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_i386.deb

```Now we create an initrd file and copy the file to /boot

```

cd /usr/src/linux-source-2.6.32
sudo su
mkinitramfs-kpkg -o initrd.img-2.6.32.11+drm33.2-a505 2.6.32.11+drm33.2-a505
cp initrd.img-2.6.32.11+drm33.2-a505 /boot
exit

```And we edit /boot/grub/grub.cfg , adding the following **bolded text**:
(you can use **sudo gedit /boot/grub/grub.cfg**, or your favorite text editor)

```

menuentry 'Ubuntu, with Linux 2.6.32.11+drm33.2-a505' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set a0fd8215-05f4-4c17-a7af-0d59f88e99b7
        linux   /boot/vmlinuz-2.6.32.11+drm33.2-a505 root=/dev/sda5 ro   quiet splash **acpi=copy_dsdt**
     **   initrd /boot/initrd.img-2.6.32.11+drm33.2-a505**
}
menuentry 'Ubuntu, with Linux 2.6.32.11+drm33.2-a505 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set a0fd8215-05f4-4c17-a7af-0d59f88e99b7 
        echo    'Loading Linux 2.6.32.11+drm33.2-a505 ...'
        linux   /boot/vmlinuz-2.6.32.11+drm33.2-a505 root=/dev/sda5 ro single 
        echo    'Loading initial ramdisk ...'
**        initrd /boot/initrd.img-2.6.32.11+drm33.2-a505**
}


```**OPTIONAL**
That will be enough to get everything working, but the update-manager tends to modify the grub.cfg each time it gets kernel updates or other things... so, we are going to modify one more file, just not to have to modify the grub.cfg each time.

We edit the default grub config:

```

sudo gedit /etc/default/grub

```And again, we add the **bolded text**...

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**acpi=copy_dsdt**"

```Then we update the GRUB Menu
```

sudo update-grub

```This will reconstruct the grub.cfg with the acpi=copy_dsdt option, but it will add it for all your kernels, including the original one.
Well, it's not like we are going to use other versions without that option anyway, so...

Now just reboot the machine and select the new kernel entry from your Grub Boot Menu.

That's it guys, now your Toshiba a505-s6005 will be 100% functional under Linux :)


By the way, if you want to get the temperature monitor, you need to install sensors-applet, hddtemp and acpi-support.
And to test the webcam, just install a program like cheese (sudo apt-get install cheese)

P.S.- If you can't even install the distro (black screen or something), that means you have an older version of Ubuntu 10.04 (probably a BETA or a RC version). 
The graphics chip from this laptop model  is an intel HD Graphics, and it's supported for Linux since 2.6.33 versions... the Ubuntu Team patched their 2.6.32 version for it to have the drivers working in the FINAL VERSION. So even if you have the latest RC version, it won't work... you need the final release.

Can i use this tip on my laptop toshiba M900?

I have been CPU Fan not work on my laptop

please help my toshiba is M900

Thank u

---

### Post by roger_r_cruz on 2010-08-04
Another greatful Ubuntu user here.  Thank you sir for the wonderful guide that allowed me to get around this ACPI issue on my Toshiba Satellite L505.  I used your recipe and hand tweaked the patch to include the DMI blacklist so I don't have to add the boot option to grub.  Note that I had to add my L505 to the default list given in the patch in this link:  [http://kerneltrap.org/mailarchive/git-commits-head/2010/5/20/34989](http://kerneltrap.org/mailarchive/git-commits-head/2010/5/20/34989)

I assume that other toshiba models derived from the L505 family will likely have the same problem so you will need to add your own entry to that list for the new models.  I found out my specific model by putting "acpi=copy_dsdt" in grub first and booting into Linux.  Then I used the "dmidecode" function to find the actual product name for my laptop and then I added another entry to the structure.  Piece of cake.

Below is my full patch

Thanks
Roger R. Cruz


diff -r adfe2b32f0e8 Documentation/kernel-parameters.txt
--- a/Documentation/kernel-parameters.txt
+++ b/Documentation/kernel-parameters.txt
@@ -151,6 +151,7 @@
             strict -- Be less tolerant of platforms that are not
                 strictly ACPI specification compliant.
             rsdt -- prefer RSDT over (default) XSDT
+            copy_dsdt -- copy DSDT for safe
 
             See also Documentation/power/pm.txt, pci=noacpi
 
diff -r adfe2b32f0e8 arch/x86/kernel/acpi/boot.c
--- a/arch/x86/kernel/acpi/boot.c
+++ b/arch/x86/kernel/acpi/boot.c
@@ -1694,6 +1694,10 @@
     /* "acpi=noirq" disables ACPI interrupt routing */
     else if (strcmp(arg, "noirq") == 0) {
         acpi_noirq_set();
+    }
+    /* "acpi=copy_dsdt" copys DSDT */
+    else if (strcmp(arg, "copy_dsdt") == 0) {
+        acpi_gbl_copy_dsdt = 1;
     } else {
         /* Core will printk when we return error. */
         return -EINVAL;
diff -r adfe2b32f0e8 drivers/acpi/acpica/acglobal.h
--- a/drivers/acpi/acpica/acglobal.h
+++ b/drivers/acpi/acpica/acglobal.h
@@ -93,6 +93,13 @@
 u8 ACPI_INIT_GLOBAL(acpi_gbl_all_methods_serialized, FALSE);
 
 /*
+ * Copy DSDT to a safe place? Default is FASLE.
+ * Some buggy BIOS may modify the DSDT memory when ACPI enabled.
+ * Set TRUE to copy DSDT.
+ */
+u8 ACPI_INIT_GLOBAL(acpi_gbl_copy_dsdt, FALSE);
+
+/*
  * Create the predefined _OSI method in the namespace? Default is TRUE
  * because ACPI CA is fully compatible with other ACPI implementations.
  * Changing this will revert ACPI CA (and machine ASL) to pre-OSI behavior.
diff -r adfe2b32f0e8 drivers/acpi/acpica/tbxface.c
--- a/drivers/acpi/acpica/tbxface.c
+++ b/drivers/acpi/acpica/tbxface.c
@@ -55,6 +55,8 @@
 
 static int no_auto_ssdt;
 
+static void acpi_tb_copy_dsdt(struct acpi_table_desc *table_desc);
+
 /*******************************************************************************
  *
  * FUNCTION:    acpi_allocate_root_table
@@ -486,6 +488,37 @@
 
 /*******************************************************************************
  *
+ * FUNCTION:    acpi_tb_copy_dsdt
+ *
+ * PARAMETERS:  table_desc          - table
+ *
+ * RETURN:      None
+ *
+ * DESCRIPTION: Some buggy BIOS would modify the DSDT memory on the fly,
+ *              so we copy DSDT for safe.
+ *
+ ******************************************************************************/
+static void acpi_tb_copy_dsdt(struct acpi_table_desc *table_desc)
+{
+    struct acpi_table_header *header;
+
+    header = ACPI_ALLOCATE(table_desc->length);
+    if (!header) {
+        return;
+    }
+
+    ACPI_MEMCPY(header, table_desc->pointer, table_desc->length);
+    acpi_tb_delete_table(table_desc);
+    table_desc->pointer = header;
+    table_desc->flags = ACPI_TABLE_ORIGIN_ALLOCATED;
+
+    ACPI_INFO((AE_INFO, "%4.4s (%p 0x%05X) is copied to %p",
+           header->signature, ACPI_CAST_PTR(void, table_desc->address),
+           header->length, header));
+}
+
+/*******************************************************************************
+ *
  * FUNCTION:    acpi_tb_load_namespace
  *
  * PARAMETERS:  None
@@ -496,6 +529,7 @@
  *              the RSDT/XSDT.
  *
  ******************************************************************************/
+
 static acpi_status acpi_tb_load_namespace(void)
 {
     acpi_status status;
@@ -533,6 +567,11 @@
         goto unlock_and_exit;
     }
 
+    if (acpi_gbl_copy_dsdt) {
+        acpi_tb_copy_dsdt(&acpi_gbl_root_table_list.
+                  tables[ACPI_TABLE_INDEX_DSDT]);
+    }
+
     (void)acpi_ut_release_mutex(ACPI_MTX_TABLES);
 
     /* Load and parse tables */
diff -r adfe2b32f0e8 drivers/acpi/bus.c
--- a/drivers/acpi/bus.c
+++ b/drivers/acpi/bus.c
@@ -67,6 +67,44 @@
     {},
 };
 
+static int set_copy_dsdt(const struct dmi_system_id *id)
+{
+    printk(KERN_NOTICE "%s detected - "
+        "force copy of DSDT to local memory\n", id->ident);
+    acpi_gbl_copy_dsdt = 1;
+    return 0;
+}
+
+static struct dmi_system_id dsdt_dmi_table[] __initdata = {
+    /*
+     * Insyde BIOS on some TOSHIBA machines corrupt the DSDT.
+     * [https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)
+     */
+    {
+     .callback = set_copy_dsdt,
+     .ident = "TOSHIBA Satellite A505",
+     .matches = {
+        DMI_MATCH(DMI_SYS_VENDOR, "TOSHIBA"),
+        DMI_MATCH(DMI_PRODUCT_NAME, "Satellite A505"),
+        },
+    },
+    {
+     .callback = set_copy_dsdt,
+     .ident = "TOSHIBA Satellite L505D",
+     .matches = {
+        DMI_MATCH(DMI_SYS_VENDOR, "TOSHIBA"),
+        DMI_MATCH(DMI_PRODUCT_NAME, "Satellite L505D"),
+        },
+    },
+    {
+     .callback = set_copy_dsdt,
+     .ident = "TOSHIBA Satellite L505",
+     .matches = {
+        DMI_MATCH(DMI_SYS_VENDOR, "TOSHIBA"),
+        DMI_MATCH(DMI_PRODUCT_NAME, "Satellite L505"),
+        },
+    }
+};
 
 /* --------------------------------------------------------------------------
                                 Device Management
@@ -812,6 +850,12 @@
 
     acpi_gbl_permanent_mmap = 1;
 
+       /*
+        * If the machine falls into the DMI check table,
+        * DSDT will be copied to memory
+        */
+       dmi_check_system(dsdt_dmi_table);
+
     status = acpi_reallocate_root_table();
     if (ACPI_FAILURE(status)) {
         printk(KERN_ERR PREFIX
diff -r adfe2b32f0e8 include/acpi/acpixf.h
--- a/include/acpi/acpixf.h
+++ b/include/acpi/acpixf.h
@@ -62,6 +62,7 @@
 extern u32 acpi_dbg_layer;
 extern u8 acpi_gbl_enable_interpreter_slack;
 extern u8 acpi_gbl_all_methods_serialized;
+extern u8 acpi_gbl_copy_dsdt;
 extern u8 acpi_gbl_create_osi_method;
 extern u8 acpi_gbl_leave_wake_gpes_disabled;
 extern u8 acpi_gbl_use_default_register_widths;

---

### Post by Veracruz290 on 2010-08-06
[I]Linux works partially with my laptop-I will post the specific problem(s)
Toshiba Satallite L505 ES5025 Installed Ubuntu 10.04
Problems: 
1) Numeric Key Pad Not Operational.
2) Mic is buggy. Sound routes thru speakers but not present on a video audio conference?
Otherwise this has been a great first experience for me with Linux. Ubuntu seems fairly straight forward.
Does anyone have a fix for either the Keypad or the Microphone?
[/I]

---

### Post by Theeus on 2010-08-07
> **donpuri said:**
> I used to have the same problem, just download drivers from:

**[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)**

(I use the 8192se driver, but my Laptop is a A505-s6033, which is exactly the same that the A505-6005, except for the processor) then unpack, move to the directory you unpacked the files and type:

Reboot your machine and Voila! your wireless is fully functional.

By the way: Any luck with the webcam? mine is working really sloooooooow...

  Oh! My apologizes, my English is really crappy... XD


I Stuck in the make part
see the screenshot
_[IMG]http://img696.imageshack.us/img696/3144/capturadetelat.png[/IMG]_[URL="http://img696.imageshack.us/img696/3144/capturadetelat.png"]
[/URL]

---

### Post by smatiauda on 2010-08-14
Works on my Toshiba L505-ES5042. Thank you!!! I've finally been able to get Linux working on my computer. You saved me from having to use Windows 7 and that is no small thing.

However, I'm getting random crashes (twice in two days). The screen goes all black and displays some text about a Glib error, and the computer freezes. I Wasn't smart enough to write down that message at the moment, but I will when (if) it happens again.

Does anybody have a hint on that?

---

### Post by nirvale on 2010-08-19
> **Lord Arctic said:**
> WARNING ::::
 
DO NOT Upgrade the Bios to 1.30 Version from the Toshiba Website, it messes up the BIOS by fixing things, 
 
IF you did not follow this advice and try to install Ubuntu (any flavor Kubuntu, Xubunto included) you get a ton of ACPI errors and a lockup with installing.
 
FIX :  Windows will not allow you to install an older version of the BIOS from within windows, BUT you can make a BIOS install CD and it WILL allow you to go back to the older (and working in Ubuntu) 1.20 version
 
[http://cdgenp01.csd.toshiba.com/content/support/downloads/sat6v120.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/sat6v120.exe)
 
is the location of the Older 1.20 Bios download, Im not sure how long that will last but it is Official Toshiba Site


yeah that's right never, never update the BIOS, never up to 1.3 version, it's a fake, it's a microsoft's anti-linux tool:lolflag:, i did update the BIOS and my ubuntu died, of course saved me the old BIOS 1.2 boot cd.

---

### Post by nirvale on 2010-08-19
> **Theeus said:**
> I Stuck in the make part
see the screenshot
_[IMG]http://img696.imageshack.us/img696/3144/capturadetelat.png[/IMG]_[URL="http://img696.imageshack.us/img696/3144/capturadetelat.png"]
[/URL]


welly, welly welly well, mmm... maybe you should create the the missing directory or verify the permissions... i don't know

anyway, there is a file inside the directory named radme.txt, i did compiled the module([r[COLOR=Red]tl8192se_linux_2.6.0017.0507.2010.tar.gz[/COLOR]]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE")) on my a505-s6005 and works fine.

take a look this, i hope so can help you, good look:p

```

========================================================================================
                II. Compile & Installation & uninstall
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:
    0. Change to Super User
       sudo su

    1. Compile driver from the source code 
       make

    2. Install the driver to the kernel
           make install
           reboot

    3. uninstall driver
       make uninstall

========================================================================================
                III. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:
<<Method 1>>
    1. Install driver like II. and reboot OS
    2. Wireless will brought up by GUI, such as NetworkManager
    3. If Wireless is not brought up by GUI, you can use: 
       ifconfig wlan0 up 
       Note: some times when you have two wireless NICs on your computer,
         interface "wlan0" may be changed to "wlan1" or "wlan2", etc. 
         So before "ifconfig wlan0 up", you can use "iwconfig" to check
         which interface our NIC is.



```

---

### Post by donpuri on 2010-08-20
> **Theeus said:**
> I Stuck in the make part
see the screenshot
_[IMG]http://img696.imageshack.us/img696/3144/capturadetelat.png[/IMG]_[URL="http://img696.imageshack.us/img696/3144/capturadeentelat.png"]
[/URL]
 
I can notice two things:
1) You have downloaded the RTL8191 instead of RTL8192se. You really want to use the 8191?
2) This may sound silly but ¿have you installed the kernel headers and basic software of compilation?

Check with nautilus if you have that directory /lib/modules and reply this message

---

### Post by GeneBrotherton on 2010-08-20
> **purelinuxuser said:**
> Hold down shift as you boot up the system, and that should bring up the GRUB menu.  Highlight the top option, press "e" to edit the kernel options, and add "nomodeset" at the end.  It won't be pretty when Ubuntu boots up, but it should work.

If anybody doesn't mind, I'm going to post a HOWTO on this in the Tutorials & Tips forum.  Also, there is no need to recompile the kernel- you can use the kernel 2.6.35 packages at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/").  Then just add the "copy_dsdt" option like described above.

PureLinux, do you believe this method work on the A505 6025 model?

Many thanks for the details of working around these issues!!

---

### Post by syntheticdream on 2010-08-23
long time reader, first time writer...
I am by definition a linux noob, have been playing around with it here and there for the last few years, I am a casual user..

Here is my problem:
I have a Satellite a500, at first I received a blank screen after selecting to boot live cd, ctrl+alt+dlt worked and I could restart the system. I was able to successfully boot up the Live 10.04 cd (usb) using 'live acpi=off" at the boot prompt. It looked alright, wireless was working, I didn't explore too much... I installed ubuntu 10.04 from the live desktop...

I boot up the new system, and received a blank screen, I tried acpi=off at the end of the boot options, I used nomodeset, and acpi=noirq..hoping to boot up the system and embark on compiling the kernel and setting everything up as presented in the howto... (I have the insyde 1.20 BIOS installed...)

Basically, I am unable to get passed the blank screen after booting up installed ubuntu 10.04 system on toshiba a500... 

Does anyone have any suggestions? Please, any help or direction would be much appreciated...

I tried 9.10 and it was not able to read the system off the USB, I am not entirely sure, at this point really wishing I had not bought a toshiba :-\

---

### Post by smatiauda on 2010-08-27
> **nirvale said:**
> yeah that's right never, never update the BIOS, never up to 1.3 version, it's a fake, it's a microsoft's anti-linux tool:lolflag:, i did update the BIOS and my ubuntu died, of course saved me the old BIOS 1.2 boot cd.

I did upgrade to 1.3 BIOS, and Ubuntu 10.04 is running OK, with the patched kernel mentioned in this thread. Is there any reason I should downgrade?

PS. Earlier I mentioned random crashes. It happened only a few times more, and then it seems it got fix by itself for no apparent reason.

---

### Post by markos7007 on 2010-09-20
does anyone know how to avoid installing the x.x.x.15+drm33.5-a505 and install the x.x.x.11+drm33.2-a505 instead. Ive gotten this to work before way back before i deleted it(barely used it and was used to windows) but that was when x.x.x.11+drm33.2-a505 was thee kernel being installed now for some reason im getting x.x.x.15+drm33.5-a505 during the installation. 

Im using a toshiba a505 s6005

Any Ideas?

---

### Post by raptura on 2010-09-21
I've got the same problem as you, markos, I haven't figured it out either.

---

### Post by raptura on 2010-09-23
Markos, and to anyone else who is interested. I also have a Toshiba a505-s6005 and was having the same problems. I got desperate, so I followed the tutorial on post #11 of this thread anyway. My computer now works, so I must have done something right :). The only thing is that some of the files have changed since the author of post #11 wrote what he did. Don't worry this will still work, with some modifications. Below, I have attached an open office document that shows what I did. (I was copying and pasting the commands on my terminal as I went along.) Let it be known that this method still works as of September 22, 2010.

---

### Post by markos7007 on 2010-09-25
^^^ yea i eventually got it to work the next night after reformating and reinstalling ubuntu, then compiling the a505 kernel then doin it all over again and agian because it wouldnt work.  I dont no what i did differently the last time but it finally worked.  But thanks for the upload might use it if something goes wrong with my kernel in the future.

---

### Post by markos7007 on 2010-10-01
just wondering will this work for the new Ubuntu release 10.10?

---

### Post by SporkWitch on 2010-10-07
Attempting this for one of the L505D series (the turion64x2 + ATI one that came out on Win7 launch day).  I'm running into many warnings while compiling the kernel.  It's still in-process now, but I tried the older ACPI fix, also had a ton of warnings, and it looked like the compile completed successfully, but when I went to the next step it said there was no makefile.

Will update once this compile finishes and hopefully it works.  Really annoying not having all the various things work thanks to ACPI.

On an aside, has anyone found a fix for DVD playback problems?  I read the KB article on the wiki and it seems like I have the necessary stuff installed for DVD playaback, but it's exceedingly choppy (5-10 seconds to buffer 1-2 seconds of video on the Iron Man 2 DVD that comes with the blu-ray 3-pack), and I don't seem able to activate DMA on sr0 (and in fact, none of the instructions mention a case of an optical drive coming up as sr*, only as hd or one other).

---

### Post by SporkWitch on 2010-10-07
Well, was able to actually use the kernel and boot this time, so that puts me ahead of the last attempt.  Performance in general is choppy and unreliable using the "fix" and window effects do not display (such as wobble, etc.).  That being said, it DOES boot the system, which using the normal kernel is not possible unless acpi=off.

Will try some workarounds tomorrow, too tired at the moment (damn switching back to day shift >_<).

---

### Post by smatiauda on 2010-10-11
> **markos7007 said:**
> just wondering will this work for the new Ubuntu release 10.10?

I tried booting the new Ubuntu 10.10 desktop amd64 from a CD on my Toshiba Satellite L505-ES5042 and still no luck... the same error appears again... Will someone ever fix it? 

I'm running ubuntu 10.04 with the patched kernel... however, it isn't trouble free. Random crashes happen every now and then.

---

### Post by moomoo5000 on 2010-11-14
I am completely new to Linux and this is my first install, so bear with me please. :]
Tried wubi on my Satellite l505D running Windows 7, didn't work. Got a lot of hex errors on a black screen, then had to restart.
Running Ubuntu off the install cd I burned onto a blank cd now.
Right after the first line of code I started getting errors saying the package may be obsoleted or missing. Screenshot:[http://imgur.com/ZITon.png]("http://imgur.com/ZITon.png")
Am I just being a helpless newbie? I hope not.
Thanks for any help!

---

### Post by myk02k on 2010-11-30
I have a Toshiba A505 and have only experienced issues with keystrokes FN & Super not being recognized. xev & dmesg do not recognize these keystrokes either. I attempted to use the patch posted by the OP with the newest kernel to no avail. If the ACPI issue mentioned in this thread is the relevant problem I'm experiencing, is there a simpler fix out now that there is a newer kernel, or do I have to revert to the old one?

---

### Post by myk02k on 2010-12-01
The problem I had with lost function of the FN & Super key has been resolved. The "acpi_osi=Linux" option added to grub was the culprit. Once removed, functionality of these keys came back.

---

### Post by Solumin on 2011-01-08
I'm trying to use the guide that's posted on page 2, but I'm running into problems.  I have Satellite A500, so I think that fixing this should be similar to fixing the other Toshiba laptops.

The first error happens here:
```

sudo apt-get install linux-source-2.6.32

```The ouput:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-source-2.6.32
E: Couldn't find any package by regex 'linux-source-2.6.32'

I tried using linux-source-2.6.35 but I ran into problems with missing files. Am I missing a repository or something that I can download the correct source from?

---

### Post by nirvale on 2011-01-10
> **Solumin said:**
> I'm trying to use the guide that's posted on page 2, but I'm running into problems.  I have Satellite A500, so I think that fixing this should be similar to fixing the other Toshiba laptops.

The first error happens here:
```

sudo apt-get install linux-source-2.6.32

```The ouput:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-source-2.6.32
E: Couldn't find any package by regex 'linux-source-2.6.32'

I tried using linux-source-2.6.35 but I ran into problems with missing files. Am I missing a repository or something that I can download the correct source from?

ok, do not worry, the matter is your sintaxis i think, because depends of your kernell version (i don't think that you are looking for 2.6.32 kernel, if you have amaverick 10.10 installed, your kernel version should be up to 2.6.35), anyway you can open in the next route SYSTEM-ADMINISTRATION-SYNAPTIC,  and type linux-source, netx in the list select to install linux-source including linux-source-2.6.35* or the version installed on your laptop, to know the kernel version installed can typing in terminal: 
```
uname -r
```another way could be... mmm

typing in terminal:

```
sudo aptitude install linux-source
```:D

if you still on 2.6.32 the kernel sources  are in the link below 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")

finally, you should upgrade to maverick 10.10 because the wifi, usb, energy, cpu... probably is now supported on 10.10

best regards:popcorn:

---

### Post by Solumin on 2011-01-10
Thank you!  I'm using 10.04 (I think...kernel version is 2.6.35-24-generic) so I was a little confused about why the guide called for 2.6.32.  I think I managed to finagle my way through it this time, so we'll see...

Full ACPI support for Toshiba laptops is not part of 10.10 from what I've seen.  I hope it will be in 11.04; I'm fond of Toshiba laptops, but this is just ridiculous.

Edit:  So I get as far as compiling the actual kernel.

```
fakeroot make-kpkg --initrd --append-to-version=-a505 kernel_image kernel_headers
[I]...
Several hundred successfully compiled files later...
...[/I]
CC      drivers/acpi/acpica/tbxface.odrivers/acpi/acpica/tbxface.c:58: error: conflicting types for ‘acpi_tb_copy_dsdt’
drivers/acpi/acpica/actables.h:112: note: previous declaration of ‘acpi_tb_copy_dsdt’ was here
drivers/acpi/acpica/tbxface.c: In function ‘acpi_tb_load_namespace’:
drivers/acpi/acpica/tbxface.c:593: error: void value not ignored as it ought to be
make[4]: *** [drivers/acpi/acpica/tbxface.o] Error 1
make[3]: *** [drivers/acpi/acpica] Error 2
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.35'
make: *** [debian/stamp/build/kernel] Error 2
```Since make-kpkg fails, I can't finish this...

EDIT: ](*,)
turns out that booting with "acpi=copy-dsdt" is all that I needed.  You were right nirvale, buggy BIOS support is included in 10.10.  I wish I had known this several months ago.  Razm-frazm....
Well hey, at least it's working now :D

---

### Post by mpk213 on 2011-01-21
Hi, I just purchased a L505D-GS6000.  I've installed Ubuntu 10.10 with out a problem, however my wireless and wired is not working right and I don't think the cpu fan works either.  

Wired hardware is recognized but can't get a connetion.  Wireless card is being recognized, when I try logging into a wireless netowrk it asks me for the passoword then it disconnects after approx. 15 seconds or conencts for a very short time and looses connection without any notification.

I saw that kmullins had success with the same laptop (post #41) but with Ubuntu 10.04.  Would the same solution work with 10.10 or should I just try my luck with Ubuntu 11 in a few months?

Please help.  I've been waiting for 2 years to get a new laptop to start playing with Ubuntu.

---

### Post by nirvale on 2011-01-24
please check your network cards, if your lap have a realtek, you should download and compile the code from realtek.com.

---

### Post by angryelephant on 2011-02-15
I have a Toshiba satelite T235D. Running amd64. I had no issues with 10.04. After upgrading to 10.10 I get a blinking cursor and stall right after the grub menu. acpi=copy_dsdt does not fix it. acpi=off allows me to boot, without suspend and the fan constantly running.

I tried installing 2.6.36 from packages. I still get a stall right after the boot menu, except when using acpi=off, but now I get some text saying that there is a PNP PCI memory conflict.

any recommendations?

---

