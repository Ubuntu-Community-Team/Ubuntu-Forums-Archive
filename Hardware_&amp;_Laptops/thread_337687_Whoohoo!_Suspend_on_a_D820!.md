---
title: "Whoohoo! Suspend on a D820!"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by mixonic on 2007-01-13
Ok, so the very first time I tried to hibernate my D820 everything went swimmingly.  The second time, and every time I went to suspend, everything broke.  Lights would come on, but the screen was blank, and no input would fix it.  Sometime I can get a terminal, but reboot doesn't seem to...well...reboot.

But there is a light.  Someone wrote this suspend script:

```
#!/bin/sh

# discover video card's ID
ID=`lspci | grep VGA | awk '{ print $1 }' | sed -e 's@0000:@@' -e 's@:@/@'`

# securely create a temporary file
TMP_FILE=`mktemp /var/tmp/video_state.XXXXXX`
trap 'rm -f $TMP_FILE' 0 1 15

# switch to virtual terminal 1 to avoid graphics
# corruption in X
chvt 1

# write all unwritten data (just in case)
sync

# dump current data from the video card to the
# temporary file
cat /proc/bus/pci/$ID > $TMP_FILE

# suspend
echo -n mem > /sys/power/state

# restore video card data from the temporary file
# on resume
cat $TMP_FILE > /proc/bus/pci/$ID

# switch back to virtual terminal 7 (running X)
chvt 7

# remove temporary file
rm -f $TMP_FILE

```

That script there, that will reliably put my D820 into ram sleep.  I can live without hibernate for now, but clicking on the system menu's suspend button, and my Fn key, would be great.

How can I use that script for sleeping my laptop?  Or, are there settings in /etc/default/acpid that I can change to match what that script is doing?  I'm an experienced linuxer, but all the Ubuntu custom stuff in /etc/acpi is a little tough to navigate.

Hardware detail:
  Nvidia card with nvidia drivers
  intel3945 wireless
  core 2 duo
  WUXGA HD screen

---

### Post by mixonic on 2007-01-14
Hm, seems to be DPMS that crashes the display.  While installing brightsides I've been testing the DPMS standby suspend and off settings, and all three crash my display (thought I can reboot X with crtl-alt-bckspace still).

So I wonder what happens when I disable it. here goes.

---

### Post by z08595 on 2007-02-04
mixonic,

I also have a d820, although for only about a week.

Exactly where do you install this script?  Do you have to manually execute it each time you want your computer to suspend, or are you somehow replacing the computer's default mode of suspending itself?

---

### Post by slick_rick on 2007-02-10
Are you running Dapper, Edgy, FF?  Stock kernel?

---

### Post by MikaelHolber on 2007-02-11
Works very well with my HP dv2000 to. Normal suspend worked with Efty kernel 2.6.17-10 but not with feisty... This script just made my life easier. Thanks

---

### Post by coreyw on 2008-02-18
Thanks a ton for posting this mixonic. I was ready to buy another laptop over this whole suspend issue. Using the "General Options" in CompizConfig, I mapped this script to my "XF86Standby" key. I run the script using "sudo" and added the following line to my /etc/sudoers in order to get around prompting me for my password.

%users ALL=NOPASSWD: /PATH-TO-SUSPEND-SCRIPT/suspend

I've probably ignored this post 10 times in my quest to fix the suspend issues on my D820. I finally got so frustrated that I wanted to see if your script at least worked. It's flawless so far (same night). The real test will be to see how it handles throughout the workday tomorrow.

---

### Post by coreyw on 2008-02-20
Okay, I'll have to take it back. I've been having the display crashes too. That stinks! Any updates mixonic?

---

