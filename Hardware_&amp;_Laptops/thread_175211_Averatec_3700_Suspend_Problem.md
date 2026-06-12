---
title: "Averatec 3700 Suspend Problem"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-05-13
Hello,
I am writing because I am having trouble getting suspend to work with my new laptop.
I have seen suspend working with this laptop when using the Ubuntu Live CD version 6.06.
I realised today that the suspend button had disapeared when I pressed the power button in Xorg, and that it had been available on the livecd.
Any ideas on how to diagnose this problem would be much appreciated.
Thank you for taking the time to read about my problem.
Mathieu

---

### Post by muadib on 2006-05-13
I just wanted to say that though there is no option that comes up for suspend when I hit the power button in gnome, I have found that if I run the /etc/acpi/sleepbtn.sh script, the machine goes into suspend mode and successfuly comes out of it when I hit the keyboard.
Mathieu

---

### Post by muadib on 2006-05-13
A new problem has arisen.

I believe that the fan is getting shut off after I run this script and does not turn back on, the laptop gets quite hot.

Thank you for any ideas on how to fix this.

Mathieu

---

### Post by muadib on 2006-05-13
I have further information on this.

It seems that if I run the /etc/acpi/sleepbtn.sh script a second time, the fan turns on again. This is, however, a bit of a hassle and it would be ideal if the fan was working after coming out of suspend for the first time.

Mathieu

---

### Post by muadib on 2006-05-21
I wanted to report that the script that formerly brought my laptop into suspend mode no longer works.

I am running an up to date version of Ubuntu Dapper.

Mathieu

---

### Post by muadib on 2006-06-05
I have just upgraded to the latest version of ubuntu dapper on the 5th of june, 2006 and I still have the problem of suspend not working.

The number of the packages that I am using follows:

ii  acpi                          0.09-1                        displays information on ACPI devices
ii  acpi-support                  0.84                          a collection of useful events for acpi
ii  acpid                         1.0.4-1ubuntu11               Utilities for using ACPI power management
ii  acpitool                      0.4.0-1                       a small, convenient command-line ACPI client

The kernel version that I am runnign is:
2.6.15-22-k7

Mathieu

---

### Post by muadib on 2006-06-05
After a reboot caused by an attempt to go into hibernation mode on this laptop, I have found that suspend does work with this laptop with the above software configuration.

I have not been able to get the laptop to hibernate successfuly. Has anyone had any luck with this or have suggestions on how to get things working right ?

Mathieu

---

### Post by muadib on 2006-06-14
I am now running the most recent packages for Ubuntu Dapper.

I am able to get the laptop into suspend once, but then the suspend option no longer works. The way that I am bringing the laptop into suspend mode is by clicking the suspend button at the gdm login screen.

Any help with this issue would be appreciated.

I am considering attempting to downgrade to the package versions where I know that the suspend works, though this is certainly not the most desirable sitation.

Mathieu

---

### Post by muadib on 2006-06-23
I have more information on this problem.

When I try to go into suspend mode using the gnome-power manager, suspend fails and there is a message on the console screen saying that suspend failed because it failed to stop 2 tasks.

Any help would be appreciated.

Mathieu

---

### Post by muadib on 2006-06-23
after trying acpitool -s I get the following message in syslog:

Jun 23 20:26:03 durnik kernel: [4307480.907000] Freezing cpus ...
Jun 23 20:26:03 durnik kernel: [4307480.907000] Stopping tasks: ============================================================================================================================================================================
Jun 23 20:26:03 durnik kernel: [4307486.908000]  stopping tasks failed (2 tasks remaining)
Jun 23 20:26:03 durnik kernel: [4307486.908000] Restarting tasks...<6> Strange, hald-addon-stor not stopped
Jun 23 20:26:03 durnik kernel: [4307486.908000]  Strange, hald-addon-stor not stopped
Jun 23 20:26:03 durnik kernel: [4307487.173000]  done
Jun 23 20:26:03 durnik kernel: [4307487.173000] Thawing cpus ...

Seems there are hal tasks that are refusing to be stopped.

Mathieu

---

### Post by muadib on 2006-06-24
I have solved this problem, though the solution is not ideal.

I added the following line to the video card section of my xorg.conf

 Option           "VBERestore" "true"

I added the option acpi_sleep=s3_bios to the boot prompt.

I unstalled hal which was the piece of software that was having processes that I could not kill that were stopping the machine from going to suspend. I now run the following script as root to get in and out of suspend mode with my laptop:

root@durnik:/home/mathieu# cat `which suspend.sh`
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
//////////////

If anyone has a better solution to this problem please let me know.

Mathieu

---

### Post by muadib on 2006-06-24
I am writing to repoort that I have gotten the laptop to suspend, but the solution is not ideal.

To get it suspending, I added the variables acpi_sleep=s3_bios to the kernel boot parameters.

Also, I had to add :
 Option           "VBERestore" "true"
to the video card section of my xorg.conf file.

Finaly, when I run the following script as root my laptop successfuly enters suspend to ram mode:

////
root@durnik:/home/mathieu# cat /usr/local/bin/suspend.sh
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
////

If anyone knows of a better solution please let me know.

Mathieu

---

### Post by UNHOLYwoo on 2006-06-25
I've never had too much of a problem with suspend, maybe because when i first encountered this problem, I was running breezy with Xscreensaver and it had settings for that kind of thing, but I DID have the problem where my lappy became burning hot after a resume.

One way I worked around this problem, was that first of all, in the BIOS, you can do fan learning, which is pretty simple and straight forward. Do that.

Now go into (i belive its) /etc/acpi and there should be a file in there called resume.sh. go ahead and edit the file (youll need to be root or sudo) and find the part where its comment out to #Kick the fans. From here, comment out the next lines in that section (I think there is only 3).

I would give examples on how it should look, but I dont have a system running atm to be able to do that. 

So you know, what youre doing, is setting the BIOS to take care of the fans, instead of the operating system. It works rather smoothly, and the lappy doesnt get too hot for having only one fan.

You may want to also install some sort of temperature monitoring applet into gnome that will tell you the temperature of the cpu.

---

### Post by muadib on 2006-06-25
Hello,

I am writing to report that I have been able to bring this laptop in and out of suspend mode succesfully.

There was never a problem with the hibenate script in /etc/acpi/hibernated.sh

All that was needed was to add the kernel boot option:

resume=/dev/hda2

which was my suspend partition.

There are still issues with the gnome-power-manager however,

Mathieu

---

### Post by muadib on 2006-06-25
Hello,

I am now looking to map the sleep button on this laptop to trigger either hibernation or suspend mode, I'm not sure how to proceed.

The sleep button gives the following output when I run acpi_listen:

root@durnik:/proc/acpi/hotkey# acpi_listen
processor CPU1 00000080 00000008
processor CPU1 00000081 00000000

I'd like to catch this input and have my /usr/local/bin/suspend.sh script be executed.

If anyone knows how to do this please let me know.

Mathieu

---

### Post by Watonga on 2006-07-29
I've got suspend working in my Averatec 3715-EH1.

I discovered thst suspend worked if I changed my video driver on xorg.conf from "via" to "vesa." So, in /etc/default/acip-support, I added all the modules I could think of that have to do with video to the blacklist, so that they are unloaded and reloaded when the computer resumes. 

So, to get suspend working for me, in /etc/default/acip-support I changed this:

MODULES=" "

to this:

MODULES="via dri glx glcore"

---

### Post by muadib on 2006-07-31
Thanks for the reply.

I would think that going from a via driver to vesa would be far from ideal as  the via driver will have performance advantages over vesa. Are you saying that the gnome power manager works with this laptop if you don't the via accelerated video driver ?

Thanks again for the post.

Mathieu

---

