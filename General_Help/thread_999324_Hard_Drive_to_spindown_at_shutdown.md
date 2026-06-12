---
title: "Hard Drive to spindown at shutdown?"
date: 2008-12-01
forum: General Help
---

### Post by sosaudio1 on 2008-12-01
I saw a post some time ago...not long in fact about someone who wanted to make sure his hard drives were at stop before his system shut down and I have been digging and digging. There is a config file that I edited on my laptop that I want to edit on my desktop to make that happen.

If someone could find that post and link me to it that would rock...or just point me to the correct config file and what to add in that would be awesome too

Thanks
Rich

---

### Post by gpsmikey on 2008-12-01
Here's a thread that discusses that issue.  Near the bottom, they mention a couple of utilities that may do what you want.
[http://club.cdfreaks.com/f138/turn-off-hard-disk-121536/](http://club.cdfreaks.com/f138/turn-off-hard-disk-121536/)

( google "linux turn off hard drive" found a number of promising links ).

mikey

---

### Post by sosaudio1 on 2008-12-01
> **gpsmikey said:**
> Here's a thread that discusses that issue.  Near the bottom, they mention a couple of utilities that may do what you want.
[http://club.cdfreaks.com/f138/turn-off-hard-disk-121536/](http://club.cdfreaks.com/f138/turn-off-hard-disk-121536/)

( google "linux turn off hard drive" found a number of promising links ).

mikey

Thanks for the help and that does get me in the ball-park but not exactly what I needed will search google...

There was this file that was an obscure name that carried parameters regarding the hard drives. The guy said he wasn't sure if his discs were still spinning upon shutdown. What this command did (that was added to this file of parameters) was to tell the harddrive(s) upon shutdown procedure once everything has been sent to halt, they are to spindown to stop and report stop, once there the system was told to power off and I can't remember where that is...it is what someone also called...I believe a soft shutdown or softer shutdown which will be the next thing I search for....but thanks for looking out!

Rich

---

### Post by sosaudio1 on 2008-12-01
anyone? I know I have seen it! I wish I had bookmarked it....

---

### Post by vandorjw on 2008-12-01
oops....wrong topic.

I thought you were referring to laptop parking for some reason.
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by sosaudio1 on 2008-12-02
> **cc7gir said:**
> oops....wrong topic.

I thought you were referring to laptop parking for some reason.
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)


LOL nope thanks for playing tho....

I am wanting to get the system to a point where the drives have spun down completely before the system powers off...

---

### Post by sosaudio1 on 2008-12-02
ok found it...did this on the laptop not long ago so it was in my console terminal history...

This is what gets edited

sudo gedit /etc/rc0.d/S90halt

log_action_msg "Will now halt"
        ### Added to gently shutdown the hard disk
        hdparm -f /dev/sda
        sleep 1
        hdparm -y /dev/sda
        ### End addition
	sleep 1
	halt -d -f -i $poweroff $hddown

That was what was added

I have two SDA's on the system at home so I think I will make two of these. One will say sda and one will be sdb1

So there it is

L8R
Rich

---

### Post by sosaudio1 on 2008-12-02
> **sosaudio1 said:**
> ok found it...did this on the laptop not long ago so it was in my console terminal history...

This is what gets edited

sudo gedit /etc/rc0.d/S90halt

log_action_msg "Will now halt"
        ### Added to gently shutdown the hard disk
        hdparm -f /dev/sda
        sleep 1
        hdparm -y /dev/sda
        ### End addition
	sleep 1
	halt -d -f -i $poweroff $hddown

That was what was added

I have two SDA's on the system at home so I think I will make two of these. One will say sda and one will be sdb1

So there it is

L8R
Rich

So if anyone wants to know what I did with the system....

I wanted to make sure that both drives spundown at power off

Here is the way mine looks now


log_action_msg "Will now halt"
        [COLOR="Red"]### Added to gently shutdown the hard disk[/COLOR]
        hdparm -f /dev/sda
        sleep 1
        hdparm -y /dev/sda

        hdparm -f /dev/sdb
        sleep 1
        hdparm -y /dev/sdb
        [COLOR="Red"]### End addition[/COLOR]
	sleep 1
	halt -d -f -i $poweroff $hddown

True at shutdown it takes a little longer but just making sure that the discs are finished with all the commands and done is worth it

---

