---
title: "Ditched Vista on Laptop - Ubuntu sort of running, but mostly not, please help!"
date: 2008-10-06
forum: Hardware
---

### Post by mikeguy3086 on 2008-10-06
Ok I'll get straight to the point. I put Ubuntu on my girlfriend's HP Pavilion dv5-1002nr. I was impressed that Linux came with useful software right after install. *But*, nothing really works. 

I got the ethernet card to work, by granting permission to it. I found driver's for the realtek networking and the ATI 3200 video card. After trying to install, I got errors on both.

Here are my other problems though. Can't use wireless, usb won't mount, and that's pretty much it. Oh, and is there a way to grant on all permissions at one time? Regarding the wireless, I tried a method I found online to no avail, for a dv5-600 <~ I think that was the model.

Also to mention, I need to get this figured out by Wednesday...my gf's mom is the mom from hell. 

Any help would be much much appreciated.

---

### Post by Sealbhach on 2008-10-06
It would help if you could give more information on the errors you're getting for all these problems.


.

---

### Post by mikeguy3086 on 2008-10-06
Of course I'm at work, and it's at home. But, I can for certain tell you the usb error I get is "Cannot mount drive volume".

---

### Post by Sealbhach on 2008-10-06
Try these commands in the terminal - hopefully they will allow you to mount USB attachements:

```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

Got that from here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632)


.

---

### Post by mikeguy3086 on 2008-10-06
Thank you, I will try that as soon as I get home. I think the all time biggest problem I'm having is with the wireless card actually receiving a signal. I've read a lot about people putting ubuntu onto the same laptop as I'm using, and they are having a lot of problems. Hopefully I can get this to just to work, because I'll be handing it off to my gf so I can't be there if something doesn't work.

Plus her mom, well she is a umm you know...

But just a head's up the ethernet/wireless I'm using (I think they are one in the same is a "RTL8101E". But thank you so much in advance, because this has been stressing me out for days.

---

### Post by mikeguy3086 on 2008-10-06
After much discussion with friend's, I'm also wondering if installing gOS is a better choice. My girlfriend will only be using this laptop for 4 things. 

1. Instant messaging.
2. Typing reports.
3. Pictures.
4. Internet.

As long as I can get the wireless to work, and ethernet, then all is well.

---

### Post by 2j4ez on 2008-10-06
Which wireless card is it?
Ive ditched vista on my laptop did not even boot into it first time

When i got ubuntu installed it found nothing! it took me about 1week to get every thing configured but now i can do it in about 5 mins

First thing i got to work was nvidia card which was easy
Was searching google and this forum for ages for a reply to my sound issue and wireless issue

I had to build a madwifi driver for my wireless and my sound i had to use a ibm levno driver (my laptop is a asus) I had to build a alsa driver for the sound.

anyway my laptop is now up and running fine with ubuntu

---

### Post by cariboo on 2008-10-06
You should really get your hardware problems sorted before attempting to install another OS, as the will help with problems if you do install a different distribution.

Jim

---

### Post by mikeguy3086 on 2008-10-06
Well after attempting to run gOS live off of a usb at work, I gave up on the idea of a new OS. So, I'd like to get down to business. Here is a list of the hardware that is not working. I'm using a 32bit version of Ubuntu. But I'm on a core 2 duo with 3 gigz of ram.

1. Wireless Card -(wireless does not show up, nor connect.
2. Video card - Ati Radeon HD 3200 (doesn't list proper aspect ratio).

Here is the page with all the specs actually. Maybe this will help better.
[http://reviews.cnet.com/laptops/hp-pavilion-dv5-1002nr/4507-3121_7-33088547.html]("http://reviews.cnet.com/laptops/hp-pavilion-dv5-1002nr/4507-3121_7-33088547.html")

 I have the ethernet connection working, and can go online, just not the wirless.

---

### Post by Sealbhach on 2008-10-06
Please put this in the terminal and copy and paste the output here:
```

lshw -C network
```

This will tell you what the wireless card is.


.

---

### Post by mikeguy3086 on 2008-10-06
I don't have the laptop in front of me right now, but about 2 hours I will. I'm at work, I'm very excited that you guys are helping me out so fast with this. But like I said earlier, I will be home and ready to get this stuff going, so if you could be here in like 2 hours, that would be the biggest help on earth, and that way it could be sort of a "live chat". 

Again, thank you so much!

---

### Post by mikeguy3086 on 2008-10-06
> **Sealbhach said:**
> Try these commands in the terminal - hopefully they will allow you to mount USB attachements:

```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

Got that from here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632)


.

melanie@melanie-laptop:~$ sudo mount/dev/sdbl /media/usb
sudo: mount/dev/sdbl: command not found
melanie@melanie-laptop:~$ sudo mount /dev/sdbl/media/usb
mount: can't find /dev/sdbl/media/usb in /etc/fstab or /etc/mtab

---

### Post by mikeguy3086 on 2008-10-06
> **Sealbhach said:**
> Please put this in the terminal and copy and paste the output here:
```

lshw -C network
```

This will tell you what the wireless card is.


.

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b0:f5:03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.103 latency=0 module=r8169 multicast=yes

---

### Post by Zimmer on 2008-10-06
melanie@melanie-laptop:~$ sudo mount/dev/sdbl /media/usb


typo .  sdb1  that should be  a one not a lower case L

---

### Post by mikeguy3086 on 2008-10-06
> **Zimmer said:**
> melanie@melanie-laptop:~$ sudo mount/dev/sdbl /media/usb


typo .  sdb1  that should be  a one not a lower case L

hey thank you, I'm having a problem now when it asks for my password, it won't let me type. I had this problem before...any idea why?

---

### Post by mikeguy3086 on 2008-10-06
melanie@melanie-laptop:~$ sudo mount /dev/sdb1 /media/usb
mount: special device /dev/sdb1 does not exist


melanie@melanie-laptop:~$ sudo mount /dev/sdb1/media/usb
mount: can't find /dev/sdb1/media/usb in /etc/fstab or /etc/mtab


---I tried both ways, and that is what I got.

---

### Post by Zimmer on 2008-10-06
sudo mount /dev/sdb1  /media/usb
 do not forget the space  
..this means   mount the device sdb1 (which could be the usb drive you have plugged in) to the folder  /media/usb   so you can browse the files on the usb drive.

---

### Post by mikeguy3086 on 2008-10-06
> **Zimmer said:**
> sudo mount /dev/sdb1  /media/usb
 do not forget the space  
..this means   mount the device sdb1 (which could be the usb drive you have plugged in) to the folder  /media/usb   so you can browse the files on the usb drive.


sudo mount /dev/sdb1 /media/usb
mount: special device /dev/sdb1 does not exist


Is there a way to make it so that it will automatically work everytime, without having to type into the terminal each time i connect a usb. This laptop will be out of my hands in a few days and with my gf...who knows nothing about comps.

---

### Post by Sealbhach on 2008-10-06
When you try to mount the usb as it is, what does it say?


.

---

### Post by Zimmer on 2008-10-06
at least you are typing the command correctly. Now, what sort of USB device is it ? Is it plugged in? Does an entry appear on the list of  'Places' ?
When plugged in a USB drive should automount and have an entry in Places, that is the default action for media.

As for wireless, I fear I cannot help you (I do not have a wireless router), other than to point you in the direction of a wiki entry for troubleshooting wifi.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by mikeguy3086 on 2008-10-06
It says cannot mount volume. But, for some reason, the graphic's card installed. Before I got erros from trying to do it, and now it's installing all of the updates. Maybe this might help? It recognized my network card and wireless LAN. I don't know how to check it though. I will let you know how everything goes after the updates are installed....if that even works.

Be back in a few minutes.

---

### Post by Sealbhach on 2008-10-06
> **mikeguy3086 said:**
> WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  

Hi,
these are step-by-step instructions to get your wireless working. It's a little bit of hacking but just follow the steps and you'll be OK. Just copy and paste the commands into the terminal.

Linky link here:

[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntuforums.org/showpost.php?p=5711824&postcount=6)

.

---

### Post by mikeguy3086 on 2008-10-06
Alright, Ill give it a try. This is all much appreciated. Ill let you know how it turns out.

---

### Post by mikeguy3086 on 2008-10-06
I got as far as the as the step that says "cd ~" I typed that in and it did nothing. I'm new to linux, so none of this really makes sense to me. The first two steps of installing worked.

---

### Post by mikeguy3086 on 2008-10-06
Thank you so much!!! I got it to work!!!!! wireless works!!! Now, to just get all the USB'a t work, I'll be all set!

---

### Post by mikeguy3086 on 2008-10-06
Ok I still am having a problem with my USB, but that;s fine for now. What I'm trying to find out now is how to enable javascript? I want to go to youtube to see if the sound works...etc. How would I do that?

---

### Post by NoWayBill on 2008-10-06
Multimedia... 
Link...[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Sealbhach on 2008-10-07
> **mikeguy3086 said:**
> Thank you so much!!! I got it to work!!!!! wireless works!!! Now, to just get all the USB'a t work, I'll be all set!

Well done!!

I advise start a new thread with title "Cannot mount USB" or something descriptive like that.

Also, thank the guy in the post I linked to. It's the medal-type button at the bottom right of the message.


.

---

### Post by Sealbhach on 2008-10-07
> **mikeguy3086 said:**
> Ok I still am having a problem with my USB, but that;s fine for now. What I'm trying to find out now is how to enable javascript? I want to go to youtube to see if the sound works...etc. How would I do that?

For Youtube, you need the Flash plugin. You can either install it using the menu System/Adminsitration/Synaptic Package Manager or from the terminal.

```
sudo apt-get install flashplugin-nonfree
```

Make sure you have the Multiverse package source (repository) enabled in Software Sources.

See this thread here which shows how to easily set up your multimedia add-ons:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


.

---

### Post by mikeguy3086 on 2008-10-07
Sorry I didn't update last night I fell asleep. I got flash working with youtube, I installed java also. I'm still having USB problems, but I posted that in a new thread. 

I also noticed that quicktime videos were a bit "chuggy".

....Also(seems to be a lot of also's), the built in webcam is not working, I see that on the little flash webcam app on facebook that it recognizes the camera. But as far as getting that to work, it doesn't.

---

### Post by Sealbhach on 2008-10-07
> **mikeguy3086 said:**
> 

....Also(seems to be a lot of also's), the built in webcam is not working, I see that on the little flash webcam app on facebook that it recognizes the camera. But as far as getting that to work, it doesn't.

Try installing Cheese, see if it works using that. It's a webcam app.

Glad you're making progress!:)


.

---

### Post by mikeguy3086 on 2008-10-07
Oh me too! In fact, a ton of stress has come down off of me. I didn't think to be this far at all. I mean I could hand her the comp now and it would be fine, but mostly for peace of mind I want the others to work. 

But on my lunch break I will install cheese. Thank you all for the help, I can't stress that enough.

---

### Post by Zimmer on 2008-10-07
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Handy resource for you mike....

---

