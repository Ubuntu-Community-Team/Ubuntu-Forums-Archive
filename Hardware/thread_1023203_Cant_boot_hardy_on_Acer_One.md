---
title: "Cant boot hardy on Acer One?"
date: 2008-12-27
forum: Hardware
---

### Post by ceaser_salad on 2008-12-27
Hi There

I bought an acer aspire one yesterday, and cant stand linpus. Using it is like trying to clap with your hands taped together.

I have more than a days experience though, as my girlfriend has had hers for 2 months now. 

I've got Hardy on my desktop, and I'd like to put it on here. I have the 120GB version, and I've added another gig of ram.

What puzzles me now, is that the disk I used to install hardy on my desktop, won't boot on the acer(downloaded the alternate install, no luck).(same story on my girlfriend's) I'm using an external dvd drive. I tried the linpus recovery disk, and that booted fine.

Suggestions welcome
Thanks

---

### Post by ceaser_salad on 2008-12-27
Forgot to mention, I'm using 8.4.1, if that makes a difference?

---

### Post by albinootje on 2008-12-27
> **ceaser_salad said:**
>  What puzzles me now, is that the disk I used to install hardy on my desktop, won't boot on the acer(downloaded the alternate install, no luck).(same story on my girlfriend's) I'm using an external dvd drive. I tried the linpus recovery disk, and that booted fine.

Can you try booting from a usb-stick ?
After several attempts with different usb-make-bootable software, and different usb-sticks I finally got it booting on my AAO.
My impression is that the AAO has a bit of a picky BIOS.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by teaker1s on 2008-12-27
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

secondly very active thread
[http://ubuntuforums.org/showthread.php?t=894852]("http://ubuntuforums.org/showthread.php?t=894852")

lastly I have an A150 running  first hardy then ibex.

I would suggest you check that the md5 check sum is correct and that you burned as "image" or iso and not as data cd.

If I can help any more just ask on this thread:guitar:

---

### Post by ceaser_salad on 2008-12-27
Dankie albinootje. 
I'm trying to do the USB thing now. Downloaded unetbootin, but cant find it? Must be here somewhere.
I'm really a newbie user, and can just about work my way around Hardy, so fiddling with this linpus/fedora concoction is giving me a headache!

teaker1s
I've also got the A150.
I'm sure i burnt the discs right. Used brasero on my desktop, and used the burn image feature, also checked both discs for errors. They showed up fine on my desktops file manager? 

As mentioned above, I'm a very basic user, and could use all the help I can get :-)

Thanks

---

### Post by theozzlives on 2008-12-27
you can't boot off an external CD drive.

---

### Post by ceaser_salad on 2008-12-27
?

---

### Post by albinootje on 2008-12-27
> **ceaser_salad said:**
>  I'm trying to do the USB thing now. Downloaded unetbootin, but cant find it? Must be here somewhere.


You installed it ?
Then it's in Applications -> System Tools

---

### Post by teaker1s on 2008-12-27
I installed as per the link I posted.

 I used an external usb card reader and one gb card, as the card slots on the a150 were useless for installing ubuntu.
If you can get the recovery disc to boot I'm surprised ubuntu will not boot.

---

### Post by ceaser_salad on 2008-12-27
Tried rebooting to see if I could find unetbootin. But now all I get is a black screen of death :-(

Heres a screen shot of the ubuntu CD. Does anything look out of place?

I think I should go to bed now, and try again tomorrow.

Thanks for the advice so far guys.

---

### Post by albinootje on 2008-12-27
> **ceaser_salad said:**
> Tried rebooting to see if I could find unetbootin. But now all I get is a black screen of death :-(

Heres a screen shot of the ubuntu CD. Does anything look out of place?

I think I should go to bed now, and try again tomorrow.

Thanks for the advice so far guys.

Good night!

I'm preparing a little bit for having a dual-boot on my AAO now.
Don't want to overwrite the working Ubuntu Hardy install, and I keep my /home on a SD-card.
Can't find the usb-stick now, I just tested with Unetbooting and FreeDOS on a 40 Gb usb-disk, and that booted fine.
Gonna try to boot with a Linux distribution from that usb-disk in a while.

---

### Post by ceaser_salad on 2008-12-28
Used unetbootin on my desktop to create a bootable usb drive.

Followed all the instructions on here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

After this command: mount -t vfat /dev/hda3 /cdrom, 
I get: ...failed: no such file directory

What am I doing wrong? :-)

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> Used unetbootin on my desktop to create a bootable usb drive.

Followed all the instructions on here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

After this command: mount -t vfat /dev/hda3 /cdrom, 
I get: ...failed: no such file directory

What am I doing wrong? :-)

Are you using the Alternate install CD or the desktop CD ?

```

Boot from the USB stick

Boot the computer from the USB stick. The installation can now be done as if you would be booting from the installation CD.

Mounting the USB stick as /cdrom

This step is only needed for the Alternate install CD and Ubuntu 6.10 or older.

Switch to the second virtual console during the first couple of dialogs (when asked about your preferred language for the installation etc.) by pressing the ""ALT-2"". Do the following:

* mkdir /cdrom /dev/cdroms
* cd /dev/cdroms
* ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
* mount -t vfat /dev/cdroms/cdrom0 /cdrom

```

---

### Post by ceaser_salad on 2008-12-28
I'm using the alternate. I've followed those instructions too.

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> I'm using the alternate. I've followed those instructions too.

Okay, good. 
But why are you using this then ?
mount -t vfat /dev/hda3 /cdrom

Your usb-stick is likely /dev/sda1 instead.

---

### Post by ceaser_salad on 2008-12-28
Just tried it again.

Typing ...sda1 doesnt work. So I rebooted, and tried sdb1, and it seemed to work. When I go back to the installation page, I'm told that there was an error reading from the cd rom. 
Thats why I tried the "mount -t vfat /dev/hda3 /cdrom" As it was the next command in the instruction sequence on that guide.

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> Just tried it again.

Typing ...sda1 doesnt work. So I rebooted, and tried sdb1, and it seemed to work. When I go back to the installation page, I'm told that there was an error reading from the cd rom. 
Thats why I tried the "mount -t vfat /dev/hda3 /cdrom" As it was the next command in the instruction sequence on that guide.

You're right. 
Sorry :( That howto is a little messy imho.

By the way, last night I started with trying to install Jaunty on my AA0, but it wouldn't recognise the cdrom (desktop iso).
After a while the AAO stopped working, much later I realised that the power-supply is probably broken :(

Now I vaguely remember how I did the Ubuntu Hardy install on the AAO, I've used some Ubuntu mini iso, and installed over the network.
That gave no problems during installation.

---

### Post by ceaser_salad on 2008-12-28
Silly question, but how do I set up a network, so I can try that? I've never had a need for a network, so I dont know how its done :-)

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> Silly question, but how do I set up a network, so I can try that? I've never had a need for a network, so I dont know how its done :-)

Hmm, sorry :| I meant with that : installing via/over the internet. :)

I think that this was the url I've used for creating the usb-stick : [http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive#The_Quick_Method](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive#The_Quick_Method)

Be careful with this line, and make 100% sure which /dev/sdX is pointing to your usb-device :

"sudo zcat boot.img.gz > /dev/sdb"

The minimal Ubuntu cdrom information is here :
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by ceaser_salad on 2008-12-28
Used unetbootin to write the mini.iso, and ubuntu seems to be installing fine now. Hope this works! I really wish using the CDrom was an option.

Dankie albinootje!

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> Used unetbootin to write the mini.iso, and ubuntu seems to be installing fine now. Hope this works! I really wish using the CDrom was an option.

Dankie albinootje!

No problem. You're welcome.
Geen probleem. Graag gedaan.

(You have some dutch blood in your veines ?) ;)

---

### Post by ceaser_salad on 2008-12-28
Afrikaans, I'm South African :-)

---

### Post by albinootje on 2008-12-28
> **ceaser_salad said:**
> Afrikaans, I'm South African :-)

Okay :)

---

### Post by ceaser_salad on 2008-12-31
Well, 

I got hardy up and running! Booting up takes longer than my desktop, and this netbook, is better specced :-)
There seems to be a lot of extra stuff going on between seeing the ubuntu splash screen, and the logon page(like: setting hardware clock - OK, etc).

I managed to get wifi working with madwifi. But yesterday while playing with powertop(I was just checking it out), my wifi died. 
I managed to get it to detect my neighbours networks, but not mine(I'm sitting an arms length away from my router)? 

Another thing that I miss, is the 'extra' touchpad features. The ability to scroll with the right side of the the pad,, and to double-tap and drag to highlight stuff.
How do I go about getting that to work again?

Thanks

---

### Post by albinootje on 2008-12-31
> **ceaser_salad said:**
>  I got hardy up and running! 

good :)

> 
Another thing that I miss, is the 'extra' touchpad features. The ability to scroll with the right side of the the pad,, and to double-tap and drag to highlight stuff.
How do I go about getting that to work again?


Is the Synaptics driver for X installed ? I assume that is needed.

---

### Post by ceaser_salad on 2008-12-31
Hi again.

How(where) would I find out if thats installed?

---

### Post by albinootje on 2008-12-31
> **ceaser_salad said:**
> Hi again.

How(where) would I find out if thats installed?
```

dpkg -l|grep -i synaptics

```
But I forgot that Ubuntu installs all of those xorg drivers plus this one.

Perhaps this is useful for you :

[http://ubuntuforums.org/showthread.php?t=979865](http://ubuntuforums.org/showthread.php?t=979865)
[http://ubuntuforums.org/showthread.php?t=928052](http://ubuntuforums.org/showthread.php?t=928052)
[http://sites.google.com/a/mg8.org/ubuntu-aa1/sw/scrolling](http://sites.google.com/a/mg8.org/ubuntu-aa1/sw/scrolling)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/272562](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/272562)

---

### Post by ceaser_salad on 2009-01-01
Mmmm, I wonder if its worth upgrading to 8.10? All the discussions relating issues I have, seem to be aimed at 8.10 users :confused:

I found this after typing that command:

ii  xserver-xorg-input-synaptics               0.14.7~git20070706-1ubuntu4                          Synaptics TouchPad driver for X.Org server

---

### Post by albinootje on 2009-01-01
> **ceaser_salad said:**
> Mmmm, I wonder if its worth upgrading to 8.10? All the discussions relating issues I have, seem to be aimed at 8.10 users :confused:

Hmmm, yes :| What about booting from a 8.10 "live" usb-stick to test, and see whether it will help your issues ?

> 
I found this after typing that command:

ii  xserver-xorg-input-synaptics               0.14.7~git20070706-1ubuntu4                          Synaptics TouchPad driver for X.Org server

Yes, I forgot the synaptics xorg driver is installed by default.

---

### Post by ceaser_salad on 2009-01-01
Thats ok :-) 
I'm not too keen on switching just yet.
I'd just like to iron out a few issues that are bugging me in hardy(boot time, battery life, touchpad etc), then I'll be happy :-)

---

### Post by albinootje on 2009-01-01
> **ceaser_salad said:**
> Thats ok :-) 
I'm not too keen on switching just yet.
I'd just like to iron out a few issues that are bugging me in hardy(boot time, battery life, touchpad etc), then I'll be happy :-)

I had about two hours battery life with Ubuntu 8.04, and I read that Linpus got 3 hours.
I'm curious where the difference is in.

(Now I'm waiting for a power-adapter replacement)

---

### Post by ceaser_salad on 2009-01-01
Powertop had this to say:

" Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity "

When I opened "dirty writeback centisecs", I found that the file was empty, so I didnt want mess with it.
Would it be OK to just copy and paste "echo 1500" in there?

---

### Post by albinootje on 2009-01-01
> **ceaser_salad said:**
> Powertop had this to say:

" Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity "

When I opened "dirty writeback centisecs", I found that the file was empty, so I didnt want mess with it.
Would it be OK to just copy and paste "echo 1500" in there?

/proc is kind of a "special magic" filesystem, it's a reflection of the Linux kernel.
I think you can edit the files, but echo is perhaps easier, perhaps better.

You can just do this :
```

sudo su -
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
exit

```
To test the difference, if you like it, then add the line
```

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

```
in /etc/rc.local

---

### Post by ceaser_salad on 2009-01-01
Not being very technically clued up, I don't really know how to decipher what powertop is telling me. 
So, after applying the "echo 1500..." step, this is what powertop reads(screenshot).

---

### Post by ceaser_salad on 2009-01-23
Time flies > work and stuff.

Well, I've kind of gotten used to the setup on here, in fact, I hardly use my desktop now :-) 

Did an update the other day, and madwifi died. I'm so glad I saved a page with instructions on how to get that going again. I didn't have a wired connection, so I was really lost, until I figured out how to reinstall it(finding where I put the files in the first place was the hardest part!).

Apart from changing the wallpaper, and putting wine on, I haven't gone beyond what I've mentioned in earlier posts. 

So, as the original topic has been solved, thats what I'll call it.

---

