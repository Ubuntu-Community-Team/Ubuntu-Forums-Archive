---
title: "[SOLVED] (Gutsy) CD/DVD drive problems."
date: 2008-10-12
forum: General Help
---

### Post by Vryko Lakas on 2008-10-12
I'm trying to update the family computer from Gutsy to Hardy. Gutsy was giving me too many problems before, and now this. 

I inserted an older Hardy liveCD I had lying around, but it didn't open any dialog window. I tried to reboot and use the boot options in my BIOS, but this didn't yield any results, just a blinking cursor. So I rebooted back into Gutsy and downloaded the latest .iso.
After verifying the correct hash for the new .iso, I tried to burn the 8.04.1 .iso with Nautilus' "Write to Disk..." option, but it didn't seem to recognize my disk drive (which had been working fine until today). It just calls the drive (null).
As a test, I inserted an audio CD, but it wouldn't offer to play the music or open the files. 

I ran Gnomebaker in the terminal with -v and it returns these errors:

```
~$ gnomebaker -v

** (gnomebaker:9126): WARNING **: gbcommon_get_file_as_list - Failed to get contents of file [/proc/sys/dev/cdrom/info]

** (gnomebaker:9126): WARNING **: devices_probe_busses - Failed to open /proc/sys/dev/cdrom/info

** (gnomebaker:9126): WARNING **: gbcommon_close_temp_file - Temporary file descriptor [/tmp/GnomeBaker-kyle/gnomebaker-EE91IU] could not be closed

** (gnomebaker:9126): WARNING **: devices_is_disk_inserted - ioctl failed

** (gnomebaker:9126): WARNING **: devices_eject_disk - Error opening device (null)
:~$ 
```

Some help would be greatly appreciated, since I don't have a spare optical drive lying around.

---

### Post by Vryko Lakas on 2008-10-13
Please?

---

### Post by Vryko Lakas on 2008-10-13
Pretty please?

---

### Post by Twitch6000 on 2008-10-13
You can try upgrading to hardy via sudo apt-get dist-upgrade

This will upgrade you to hardy,but be warned there is a slight chance of some bugs during this process,but it has never happened to me or anyone I know >.>.

Also for burning a .iso k3b works great.

Oh and note try not to bump to much as this does break a UF rule >.>.

---

### Post by Vryko Lakas on 2008-10-13
> **Twitch6000 said:**
> You can try upgrading to hardy via sudo apt-get dist-upgrade

This will upgrade you to hardy,but be warned there is a slight chance of some bugs during this process,but it has never happened to me or anyone I know >.>.
I really want to do a clean install to minimize the chance of any configuration errors being carried over. Maybe then my HPLIP supported printer will actually work and I won't have some of the weird boot issues I've experienced lately.

> Also for burning a .iso k3b works great.
So do Nautilus and GnomeBaker. The problem isn't what program I'm trying to use, the problem is that *my drive doesn't work/show up anymore*, even though I can see it in BIOS. 

> Oh and note try not to bump to much as this does break a UF rule >.>.
Sorry. I'm just exceedingly frustrated. I wanted this computer updated a couple of days ago and now I don't know if I have a hardware or a software problem that's keeping me from doing it. The whole reason for the update is, as I said, Gutsy keeps breaking in ways I haven't been able to get fixed. At least I didn't threaten to go back to Windows, right? 8-[
This is also the family computer, so it's not something I can just fiddle with for a week.

---

### Post by Vryko Lakas on 2008-10-13
I just got off the phone with the guy who helped me put this box together and he's pretty sure the optical drive itself has gone bad since it can't boot the LiveCD. Not want I wanted to hear by a long shot, but at least I don't have to pull my hair out trying to fix the problem anymore. Hopefully it's still under warranty so I can get a fix/replacement. In the meantime I think I'll order a new drive to install, keep the other as a back-up once it gets fixed. 
Sorry if I've made a nuisance of myself. I appreciate the suggestions of those who tried to help.

---

