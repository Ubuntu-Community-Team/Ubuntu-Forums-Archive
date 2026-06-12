---
title: "Can now start GUI after install"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Martin_sensei on 2009-10-31
I hope someone can help...

I have just installed Ubuntu 9.10 from fresh (I formatted a partition and installed it there)  The partition is 10GB so I believe it is enough for Ubuntu.

So I booted the live CD, then installed Ubuntu from the live session, everything went well, the install finished and I rebooted.

After the reboot I ended up with a shell prompt which flickers very badly I doesn't hear all my keystrokes, so it it impossible to log in.

It basically is a black screen with the following:

Ubuntu 9.10 martin-desktop tty1
martin-desktop login:

Any ideas what has gone wrong? Or how to get out of this?  
I can also boot in recovery mode, which gives me the same login prompt but no flickering, and still no GUI.

It is an older PC but nothing fancy:
Asus A8N SLi motherboard 
AMD 64 3200
2GB DDR RAM
2 160GB Maxtor HDDs
NVidia 9600 GT
Creative Soundblaster Audigy

---

### Post by Regele IONESCU on 2009-10-31
I made a fresh install too on an Acer Aspire 9423wsmi laptop, after I installed Windwos7. When I try to boot I get the same **flickering black screen** with tty1 and login lines. I hardly manage to type the username, but when it comes to password it types nothing.

---

### Post by ratcheer on 2009-10-31
> **Martin_sensei said:**
> 

After the reboot I ended up with a shell prompt which flickers very badly I doesn't hear all my keystrokes, so it it impossible to log in.

It basically is a black screen with the following:

Ubuntu 9.10 martin-desktop tty1
martin-desktop login:

Any ideas what has gone wrong? Or how to get out of this?  
I can also boot in recovery mode, which gives me the same login prompt but no flickering, and still no GUI.



I am having the exact same problem. We really need some help.

Thanks,
Tim

---

### Post by emigrant on 2009-10-31
in tty1
login with the username/password you gave during the installation.
then give:
```

sudo killall gdm
```then
```

sudo gdm
```

---

### Post by mshannon on 2009-10-31
Same problem here after an upgrade prompted by upgrade manager, everything went OK until after reboot. Unable to log in due to the screen flicker as it's not possible to tell if you have typed in the password correctly. For example my user name is "mick" but due to the screen flashing it does not always accept the keystrokes therefore have several atemps so get things like "mmmik" "ick" etc.

---

### Post by Martin_sensei on 2009-10-31
> **emigrant said:**
> in tty1
login with the username/password you gave during the installation.
then give:
```

sudo killall gdm
```then
```

sudo gdm
```

Thanks for your help.  I tried this and got the following:

** (gdm-binary:1757):WARNING ** Could not acquire name; bailing out

What was this supposed to do?

Cheers

---

### Post by Martin_sensei on 2009-10-31
I read somewhere that we need to update the nvidia drivers, but I have got no idea how to do this from a recovery command prompt session!

I have downloaded the drivers on the windows partition but I can not see this or mount the disk from the recovery prompt.

---

### Post by Martin_sensei on 2009-10-31
Hello all,

I sorted this!  I managed to mount a usb stick with the new nvidia drivers

```

mkdir myusb
sudo mount /dev/sdc1
sudo chmod +x myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run
sudo /myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run

```

Followed the prompts and it all worked.

---

### Post by Chow7 on 2009-10-31
> **Martin_sensei said:**
> Hello all,

I sorted this!  I managed to mount a usb stick with the new nvidia drivers

```

mkdir myusb
sudo mount /dev/sdc1
sudo chmod +x myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run
sudo /myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run

```

Followed the prompts and it all worked.

I put the driver on a USB stick but when I type   sudo mount /dev/sdc1 it says it can't find it.

---

### Post by Chow7 on 2009-10-31
Updating the nvidia driver fixed it!!

---

### Post by Crimson_Tider on 2009-11-01
> **Martin_sensei said:**
> Hello all,

I sorted this!  I managed to mount a usb stick with the new nvidia drivers

```

mkdir myusb
sudo mount /dev/sdc1
sudo chmod +x myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run
sudo /myusb/NVIDIA-Linux-x86-185.18.36-pkg1.run

```

Followed the prompts and it all worked.



I am having the same problem; how can I find out what kind of video card I have so that I can get the right driver?  I am a newbie and don't know how to do this from a command prompt.

---

### Post by Martin_sensei on 2009-11-02
Have you got Windows installed too?  The windows device manager will tell you (hopefully) about the card.

Otherwise, open up the case and have a peek...  The card model should be stamped on the graphics card somewhere, (my older ATI card had a sticked on the underside with the model and make, my NVIDIa card has the model number in big letters printed on the heatsink).

---

### Post by Crimson_Tider on 2009-11-02
> **Martin_sensei said:**
> Have you got Windows installed too?  The windows device manager will tell you (hopefully) about the card.

Otherwise, open up the case and have a peek...  The card model should be stamped on the graphics card somewhere, (my older ATI card had a sticked on the underside with the model and make, my NVIDIa card has the model number in big letters printed on the heatsink).

I don't have Windows, and I'm fairly certain without getting into the computer that it is an onboard video adapter. I mis-spoke when I used the term "video card."

---

### Post by oldos2er on 2009-11-02
> **Crimson_Tider said:**
> I am having the same problem; how can I find out what kind of video card I have so that I can get the right driver?  I am a newbie and don't know how to do this from a command prompt.
```

lspci | grep VGA
``` should show you what you need to know.

---

### Post by Crimson_Tider on 2009-11-03
> **oldos2er said:**
> ```

lspci | grep VGA
``` should show you what you need to know.

Okay, I did that and found out that I have an Intel 82845G integrated.  I went to the Intel site to download the driver, and it says that I should obtain "precompiled driver packages from my Linux distribution vendor." So where do I get these?

Sorry to be such a pain!

---

### Post by Martin_sensei on 2009-11-04
Ah,

I'm affaid I don't know much about the intel drivers as I have only set up ATI and NVIDIA cards before.

I did find this webpage which links to some downloadable intel drivers.  Perhaps worth a try:

[http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")

Sorry I can't be of more help!

---

### Post by Crimson_Tider on 2009-11-04
> **Martin_sensei said:**
> Ah,

I'm affaid I don't know much about the intel drivers as I have only set up ATI and NVIDIA cards before.

I did find this webpage which links to some downloadable intel drivers.  Perhaps worth a try:

[http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")

Sorry I can't be of more help!

The page at that link says

"Compiling and/or upgrading graphics drivers in Linux is a complex and error-prone task. Here is a user guide for how to build the driver from scratch. If you are not experienced doing this, we recommend that you get precompiled packages from one of the many Linux distributions."

That's definitely referring to me.

I found a driver at

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=865&lang=eng)

but it has a date of 2004, so I bet that won't help me.

---

### Post by Martin_sensei on 2009-11-04
Ah, sorry!

Well it may be worth giving the ones from Intel a go, so you can at least startup x.

---

### Post by SL666 on 2009-11-04
I had this issue also,

solved by installing the restricted drivers for my video card (nvidia 8800gt) -  package is nvidia-glx-180.

I then also had to rebuild my xorg.conf as nvidia-settings would crash when trying to save the settings (i run two screens) so i had to run nvidia-xconfig to replace the xorg.conf.

this solved my issues.

---

### Post by Crimson_Tider on 2009-11-05
> **Martin_sensei said:**
> Ah, sorry!

Well it may be worth giving the ones from Intel a go, so you can at least startup x.

Okay, so I downloaded the driver (the one from 2004) to my USB drive. How do I install that driver from the command prompt? I know I need to mount the USB drive first, right? And to do that, I've got to find out what my device is named in the filesystem, right?

So, I tried
```
sudo fdisk -l
```
and it told me my USB device is recognized as /dev/sdb1.

Okay, so then I tried
```
sudo mkdir /media/external
```
so that I would have a directory to mount it to, but the response I get is
"mkdir:cannot create directory '/media/external':read-only file system"

What do I do from here?  Keep in mind that I'm a newbie and I'm not totally certain of what I'm doing here.

---

### Post by Martin_sensei on 2009-11-05
That's a bit strange.  How have you logged on?  I booted into Ubuntu 9.10 recovery mode, then did a resume normal boot.

That took me to a tty1 login prompt (but without the flickering).

I logged in as me, then I was able to create a directory in /media and mount my usb stick.

Cheers

Martin

---

### Post by Martin_sensei on 2009-11-05
Also check the output of "mount"

Is your linux partition ext4 (or FAT, or NTFS)? Does the output show any "ro" flags? This would mean the partition is read only.

---

### Post by Crimson_Tider on 2009-11-08
> **Martin_sensei said:**
> Also check the output of "mount"

Is your linux partition ext4 (or FAT, or NTFS)? Does the output show any "ro" flags? This would mean the partition is read only.

Output of mount:
```
/dev/sda1 on / type ext3(rw, relatime, errors=remount-ro
```

Then it has several more lines that all have the form

"none on" something, something, something "(rw)" or "(rw, something)"

Of course, when I use the word something above, I'm just talking about several different directories or whatever.

---

