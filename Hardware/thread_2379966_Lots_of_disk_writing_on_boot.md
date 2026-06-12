---
title: "Lots of disk writing on boot"
date: 2017-12-11
forum: Hardware
---

### Post by caterhamfan on 2017-12-11
Hello,

I'm still very new to Ubuntu. Not a pro, so please be easy on me ;)

I'm running Ubuntu 16.04 LTS, on a custom built laptop from pcspecialist.co.uk
Since I've purchased the laptop however, I've had slow booting (after entering my password). Lots of disk reading and writing. My laptop makes a horrible noise whilst doing so. Even through some moments when it is quieter! Like it is now, it's noticeably loud. Is this just an Ubuntu thing?

Are there things I can do to check if something is abnormal/speed up the process? Some commands or apps?

Another issue is hibernate. Most of the time when I boot back into my laptop from hibernation. It takes forever to get back in ~5-10 minutes and lots of heavy disk reading and writing.

I'd be grateful if someone can assist me with this.

Thank you,

---

### Post by ajgreeny on 2017-12-12
Doesn't sound normal at all if it happens every time.

Next time you boot up, whilst the machine is chattering away, run the command ```
top -n 1
``` and then copy the output back here for us to see.

The machines from PCSpecialists, whislt not specifically made for Linux are usually very good as long as you have chosen the correct hardware for the OS, which you appear to have done.

It is worth running the SMART disk test from the hamburger icon of the Disks application, which should be installed and available from the dash (top icon of the launchbar).

---

### Post by caterhamfan on 2017-12-12
Thank you,
Here's the output. 

[ATTACH=CONFIG]277815[/ATTACH]1

I see Opera was using a lot of CPU there. I ran it again a little after boot.

2

[ATTACH=CONFIG]277816[/ATTACH]


I'm running a self-test now. Do these take quite long generally?

Thank you,

---

### Post by ajgreeny on 2017-12-12
By self-test do you mean the SMART disk test?

It is a long time since I used that and it was on a small disk which did not take too long to report, but on a large 1GB disk I imagine it may take a while?  Wait for others to comment as they may know a lot more than I do.

Unfortunately I can not help with opera as I've never used it but it certainly seems to be using a lot of resources; what were you browsing at that time and how many tabs had you open?

---

### Post by ajgreeny on 2017-12-13
Another idea that comes to me; you said this disk activity is happening at boot so I wonder why you have several opera processes running at that time.

Do you have opera start always at boot, or do you save you sessions when shutting down?

---

### Post by caterhamfan on 2017-12-18
Sorry for the delay.

I did mean the SMART disk test yes. By the way, I didn't mean opera was the source of the problem sorry for any confusion. It just so happened that I decided to boot Opera straight away! This happens if I boot Opera straight away or not. 

I don't have Opera running at boot. I will run another output (without Opera) and report back when this is done.

**EDIT: here is the output**
[ATTACH=CONFIG]277867[/ATTACH] 

Thank you so much.

---

### Post by mörgæs on 2017-12-20
Intel has released a lot of bug fixes for Skylake processors in Buntu 17.10.
Have you tried in a live boot if this version is more stable?

---

### Post by sccman on 2017-12-20
Hmm if Opera isn't the problem then it might be another program that isn't using a lot of CPU cores.

Try running **iotop** to show us how your disk is being used:

```
sudo apt install iotop && iotop
```

---

### Post by caterhamfan on 2018-02-24
> **sccman said:**
> Hmm if Opera isn't the problem then it might be another program that isn't using a lot of CPU cores.

Try running **iotop** to show us how your disk is being used:

```
sudo apt install iotop && iotop
```

Thank you all for your help! Sorry for the immense delay.

I have yet to run a live boot with 17.10. 
The problem still persists. I have run iotop. The last image represents what happens when I open Opera Browser.

I don't really know if something is going wrong from the data pictured. I'd be grateful if someone can tell me if something is up. I notice the disk write was in the 400's at times though.

[ATTACH=CONFIG]278646[/ATTACH][ATTACH=CONFIG]278647[/ATTACH]

This last one is upon me firing up Opera:

[ATTACH=CONFIG]278648[/ATTACH]

I would be grateful for any assistance. I can not tolerate the slow booting speeds, much longer. It also happens when opening a browser with lots of tabs, or when returning from hibernation. 

Thank you,
Matthew

---

### Post by mörgæs on 2018-02-25
> **caterhamfan said:**
> 

I have yet to run a live boot with 17.10.


Why not? You've had months.

It's not only a matter of trying a release suitable for your hardware it's also a matter of trying a pristine release without Dropbox. As you can see in the screenshots Dropbox is making a lot of activity.

---

