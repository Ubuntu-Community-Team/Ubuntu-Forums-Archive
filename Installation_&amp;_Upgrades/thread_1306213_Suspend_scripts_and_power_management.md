---
title: "Suspend scripts and power management"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by entropic_existence on 2009-10-30
Hi everyone,

On the dell mini 9 suspend will work in 9.10 only if you first unmount any mounted sd cards. Its a little bit of a pain but at least you should be able to fix it by obviously unmounting your card before suspending.

I have been going through forum posts around the web all morning and I am finding it increasingly confusing as to what exactly happens in 9.10 when you suspend. Lots of power-management stuff has been moved around, there are several scripts that look like they should be involved in suspending scattered around (/etc/acpi/sleep.sh /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux, etc). What I am looking to do is add a simple umount /path/to/SD_Card command in the relevant script so that it is unmounted before I initiate a suspend action, that way I don't need to remember to manually unmount the drive everytime.

Where should I do this? Anyone know the sequence of calls that happen when you initiate a suspend now under 9.10?

Any and all help would be appreciated.

---

### Post by entropic_existence on 2009-11-01
No ideas? No one has any idea what exact scripts are called now with the new power management scheme when you initiate a suspend? I'm having trouble even finding the right documentation of where to look.

---

### Post by Mjoln on 2009-11-29
Hi,

In /etc/pm/sleep.d/ you can find your suspend/sleep/hibernate scripts. Just put this in there:

```
case "$1" in
    hibernate|suspend)
        umount /path/to/SD_Card
        ;;
    resume|thaw)
        mount /path/to/SD_Card /mount/point/
        ;;
    *) exit 0
        ;;
    esac
```Now your SD card is unmounted every time you suspend or hibernate your computer and mounted back when you resume.

---

### Post by entropic_existence on 2009-11-29
> **Mjoln said:**
> Hi,

In /etc/pm/sleep.d/ you can find your suspend/sleep/hibernate scripts. Just put this in there:

```
case "$1" in
    hibernate|suspend)
        umount /path/to/SD_Card
        ;;
    resume|thaw)
        mount /path/to/SD_Card /mount/point/
        ;;
    *) exit 0
        ;;
    esac
```Now your SD card is unmounted every time you suspend or hibernate your computer and mounted back when you resume.

Thanks for your reply. The only issue is that the main suspend/hibernate scripts are not located in /etc/pm/sleep.d/ anymore, although there are accessory scripts located there. In my case one for wpa_supplicant, one for telling grub that resume was successful and one for handling unattended upgrades prior to hibernating. 

I have placed a script in there for handling the SD card prior to suspend or hibernate but cannot locate the main suspend script that would call this one.

---

### Post by uomiarz on 2009-11-30
Hi,

Did you get it to work? I need to stop mythtv-backend before going to sleep and then restart it on resume otherwise karmic will not suspend.

thx

---

### Post by entropic_existence on 2009-11-30
> **uomiarz said:**
> Hi,

Did you get it to work? I need to stop mythtv-backend before going to sleep and then restart it on resume otherwise karmic will not suspend.

thx

I haven't really tweaked with it anymore to be honest since I'm not sure where the main scripts are located. Its also been relatively easy enough to unmount my SD card myself before I put the netbook into suspend.

---

### Post by ZOMGxuan on 2009-12-01
[https://wiki.edubuntu.org/AcpiSupportDeprecation]("https://wiki.edubuntu.org/AcpiSupportDeprecation") appears to say that resume and suspend scripts, which were originally stored in /etc/acpi/{suspend,resume}.d, are now stored in /usr/lib/pm-utils/sleep.d/. Try placing the script there instead.

---

### Post by Mjoln on 2009-12-11
I tried putting my own script (to unmount an external usb hdd) to both /etc/pm/sleep.d/ and /usr/lib/pm-utils/sleep.d/ and it worked fine in both cases. Why exactly are there two paths for suspend/hibernate scripts?

---

### Post by erlguta on 2010-02-07
How Mjoln says, it can be solved putting one script in /etc/pm/sleep.d/ or /usr/lib/pm-utils/sleep.d/

The problem is with the line:
```

/path/to/SD_Card

```
as I don't know how the SD_card name is going to be...because each card has a different name. How can I to do a generic script whatever the name is, for the card to insert?

PD:
This is the bug related with this:
[https://bugs.launchpad.net/bugs/436729](https://bugs.launchpad.net/bugs/436729)

If it is so easy to solve this i don't know why it is stil unasigned...

---

