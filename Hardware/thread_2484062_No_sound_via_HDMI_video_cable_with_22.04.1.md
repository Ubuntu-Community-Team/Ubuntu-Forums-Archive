---
title: "No sound via HDMI video cable with 22.04.1"
date: 2023-02-16
forum: Hardware
---

### Post by vbcoen on 2023-02-16
I have a tuner card from Turbosight a tbs6205 DVB-T2 card.
Now running older versions including mythbuntu from 16 and upgrading last to 20.04 LTS I got it all to work having downloaded the tbs kernel media v4l set (from them) that contans among many others their drivers.

From Sound I selected a driver that description had HDMI output.

All using a SSD boot drive :

Cutting a longish story short when I upgraded 20.04 to 22.04.1 then installed mcp (myth command panel), set the version of myth (31) and installed it via apt then rebooted it failed to start with a failure of a myth driver and could not progress even when rebooting multi times SO
I installed ubuntu desktop and tried again this had the same issues as the next part of the story :

I installed xubuntu (which installs Gnome any way), downloaded the tbs v4l drivers and prepared for a compile on a HDD via /mnt mounted via a cron job every @reboot along with another partition for the recording etc for mythtv.

Next went in to the Sound app via top of screen and was able to select a HDMI o/p driver.

Next compiled the v4l drivers and installed them, then rebooted.
Confirmed that the Tuner was now present by sudo dmesg | grep frontend which shows :
[    3.705773] TBSECP3 driver 0000:01:00.0: DVB: registering adapter 0 frontend 0 (TurboSight TBS 6205 DVB-T/T2/C )...
[    3.948497] TBSECP3 driver 0000:01:00.0: DVB: registering adapter 1 frontend 0 (TurboSight TBS 6205 DVB-T/T2/C )...
[    4.107233] TBSECP3 driver 0000:01:00.0: DVB: registering adapter 2 frontend 0 (TurboSight TBS 6205 DVB-T/T2/C )...
[    4.350672] TBSECP3 driver 0000:01:00.0: DVB: registering adapter 3 frontend 0 (TurboSight TBS 6205 DVB-T/T2/C )...

Went into Sound but this time there is NO HDMI options and for the many are marked as "unplugged unavailable" with just two that are but both options produce no sound when running the Test Sound option.

Now I do NOT normally have the TV speakers on as both my wife and I use headphones (different types) and I also use my hearing aid bluetooth transmitter with all these adapters etc connected via the TV output jack.  Bye the way all testing was done using the hearing aid, headphones AND the TV speaker on.

 
I am guessing for version 22.04.1 the installed drivers are getting overwritten by my installing the kernel media drivers but this has never happened before with the older ubuntu versions.
I have not found a copy of the v4l drivers within ubuntu's repos but it is quite possible I have been looking in the wrong places but even then not sure using them would fix the issue.

I cannot find a setting to rescan hardware in order to download and install the correct kernel drivers which by the way is vmlinuz-5.15.0-60-generic

When booting I do NOT get the grub options to select the kernel version to boot to (within a number of seconds etc)

My main system server/desktop for normal usage and development  is Magiea v8 X64 and that on boot checks for changes to hardware, then offers a grub2 menu to select kernel before booting to last used one.
Ubuntu does not appear to have this facility .

So that the sorry tale over the last two weeks with a media system that records programs etc but cannot play back with sound

Can anyone help me as 'I' have totally run out of ideas ?

---

### Post by ajgreeny on 2023-02-16
Open up the Audio mixer from the volume icon in the panel (that should open pulseaudio volume control) and check that the appropriate HDMI connection is enabled.
See my screenshot which may show it more clearly, though I do not have any HDMI devices available at present.
The audio-mixer should show both the analogue and digital (HDMI) outputs in the right hand configuration tab

---

### Post by vbcoen on 2023-02-16
I do NOT have any listed with the words HDMI and that seems to be the problem.

---

### Post by Nattydread69 on 2023-03-05
I have the same issue after a recent update,

I found my HDMI was broken with kernel  5.19.0-35 but choosing 5.19.0-32 in grub gives working sound.

---

### Post by vbcoen on 2023-03-05
I am using the normal kernel as supplied and installed with 22.04.1 and as updated going by memory may be 5.15.0.60 (could be wrong ).
So you have installed a later version, yes.
Another issue is I do NOT get a screen offering any options via grub on boot.

I have now installed Mageia v9 beta initially as an additional disto but it crapped out when setting up the bootloader and damaging the boot drive.
I then installed Mageia v8 and had to reformat that boot SSD drive.
I will look at reinstalling ubuntu but with these issues I will consider using 20.04 instead into another partition and if that works try again with 22.04 (I have 3 partitions of around 60Gb each).

This attempt will be the fix or drop - after over ten years with ubuntu it would be a shame but it is not beginning to seriously annoy the heck out of me - I find having reached 75 my patience is a lot lower these days and I expect an operating system to well just work a lot more than ubuntu has been doing.
I went to ubuntu because of the longer life cycle as doing a update is always risky but if these attempts to sort it out fail then so be it.

 After I install 22.04  I will look for a kernel on the 5.190.35 or later so thanks for that - I assumed the problem was everything other than the kernel :(

Never had issues with them before and that's going back around 20 years.

Thanks for the hint.

---

### Post by ajgreeny on 2023-03-05
There is now another kernel version 5.15.0-67 which became available yesterday for me.

Run normal updates and see if that newer version solves your problem.
Though I had no problem with the -60 kernel it could be something related to your hardware, perhaps that turbosight card, that causes this lack of sound.

---

### Post by vbcoen on 2023-03-05
OK, a wee update -

Today a newer kernel came in along with other updates so installed all. Then rebooted and took a look at Sound -> config and low behold
I found HDMI options with one with stereo o/p, so selected that one checked in Output option and exited the sound app.
I then payed a recording and guess what Sounds cometh.

So far so good, tent I rebuilt the v4l driver set from TBS website and installed it then rebooted.
Checked that the system had found the TBS tuner card - it had then, went in to Sounds -> Config and all the HDMI options was no longer present.
Needless to say no sound output.

So guessing here it has something to do with installing the v4l modules clashing with some part of the kernel some way.

The process for building and installing the v4l modules has not changed in years so it is something to do with 22.04 and its kernel.

I am not so sure that upgrading to the 5.19 releases will fix it but I am having issues with setting up mythtv and Mageia so will install ubuntu as a refreshed partition from the /home directory which for some reason Mageia has created instead of using the boot partition - can't resize it in Mageia as it is in use even when I logged in as root who's home area is off / but I have made a backup of /home called /home2 as a small safety factor but have a feeling that when I attempt to install Ubuntu in a new partition created out of home things will go belly up - as the rest of this sorry saga.

Just getting even more deeper in the mire :(

---

