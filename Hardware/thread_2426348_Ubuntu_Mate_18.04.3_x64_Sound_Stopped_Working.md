---
title: "Ubuntu Mate 18.04.3 x64 Sound Stopped Working?"
date: 2019-09-07
forum: Hardware
---

### Post by ken0069 on 2019-09-07
This is a multi-boot system with Windows, Linux Mint 17.3 and Ubuntu-Mate 18.04.2 which I installed on an SSD to replace the outdated Mint.  Sound works fine with the other operating systems but not with Ubuntu?  

This was a new clean install of Ubuntu Mate 18.04.3 about 2 or 3 weeks ago and the sound worked then because I installed QMMP and VLC and it worked afterwards.  Then some time recently "I think" after the last update that was done, sound no longer works.  

The sound volume icon still shows up in the task bar and it's set to maximum volume and mute IS NOT CHECKED.  When I double click on it and then click sound preferences the "Output" tab under "Chose a device for sound output:" only shows Dummy Output Stereo checked?  Is this normal?  

Ennywho, can someone tell me what "Dummy Output Stereo" is and if that's the only option that should be there, and, if that's what it's suppose to be, what do I need to do to fix my sound problem?

Thanks

---

### Post by CatKiller on 2019-09-07
> **ken0069 said:**
> Ennywho, can someone tell me what "Dummy Output Stereo" is and if that's the only option that should be there, and, if that's what it's suppose to be, what do I need to do to fix my sound problem?
The dummy sound output is for when there is no other hardware - because it doesn't exist, is unsupported, or is misconfigured - so that there will always be a selected output even though it doesn't do anything.

Since you had sound at one point, it seems that it is now misconfigured: hardware failure for sound devices is possible but extremely rare. The trick is to undo whatever it was that broke it.

There's a sound troubleshooting sticky that will show you how to provide detailed information about your hardware and its configuration. That should allow someone to help identify what's gone wrong.

---

### Post by ken0069 on 2019-09-07
And might I ask where is this "Sound Troubleshooting Sticky" you speak of lis ocated?

---

### Post by CatKiller on 2019-09-07
[https://ubuntuforums.org/showthread.php?t=1885240](https://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by deadflowr on 2019-09-07
> **ken0069 said:**
> And might I ask where is this "Sound Troubleshooting Sticky" you speak of lis ocated?

Here:
[https://ubuntuforums.org/showthread.php?t=1885240]("https://ubuntuforums.org/showthread.php?t=1885240")
It's stickied in the Multimedia Software sub-forum.

ninja'd

---

### Post by oldfred on 2019-09-07
In the Multimedia subforum.
[https://ubuntuforums.org/forumdisplay.php?f=334](https://ubuntuforums.org/forumdisplay.php?f=334)

Direct link.
[https://ubuntuforums.org/showthread.php?t=1885240](https://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by ken0069 on 2019-09-12
First, guys thanks for the replies and please forgive me for not replying sooner!  In my defence, my pants have been on fire working on computers here and one for a friend and I&#8217;m just now getting caught up.  

RE: my sound card issue.......well, that&#8217;s been just a small part of what&#8217;s been going on.  I don&#8217;t like laptops for LAN gaming so I have multi boot desktop computers setup in several rooms in my house.  So when Linux Mint 17.3 reached EOL I had several systems to update.  

I had loaded Mint 19.1 in one system and was very disappointed that NTFS config and SAMBA were no longer supported.  I found the work around to install them anyway, BUT, ran into a problem when any one of the &#8220;auto-mount&#8221; drives happen NOT to be connected, ie, Mint 19.1 would stop and not boot and I didn&#8217;t find a work around for that other than booting from the Live DVD and editing fstab.  In Mint 17.3 when an auto mount drive wasn&#8217;t present a prompt would come up on the boot screen offering the option to hit &#8220;S&#8221; to skip mounting for that particular drive.  Mint 19.1 didn&#8217;t give me that option??

Having tried Ubuntu Mate 18.04 on one of them and liking that &#8220;Minimal Install&#8221; feature it has I updated all 3 systems with Ubuntu Mate 18.04.  Not long after that I started having problems with crashes and lockups, some of which required a power off reset along with the audio problem on my main box here in the shop.  I don&#8217;t know whether it is my old hardware that was causing this but it wasn&#8217;t present with Mint 19.1.

So, I fixed the sound card problem and the other problems by going ahead and installing Mint 19.2 ON ALL OF THEM!  I just turned 74 last week and I&#8217;ve found that my patience is growing shorter day by day than my potential lifespan.  In other words, life has gotten too short.

Ennywho, I&#8217;m going to need some help/info on the current Mint 19.2 auto mount problem because I need to have file sharing enabled on my network.  I&#8217;ll start another thread soon to discuss/address that issue.

And THANKS AGAIN!!

---

### Post by oldfred on 2019-09-12
You may be able to use autofs or noauto, but I am not one who uses or knows those.

       [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
use noauto if mount issues
[https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109](https://askubuntu.com/questions/1047109/how-can-i-delay-mount-of-secondary-internal-hard-drive-on-boot?noredirect=1#comment1710066_1047109)
UUID=44EC439A779EB78C /media/Shared   ntfs-3g        noauto,user,rw 0 0
sudo mount /media/Shared

---

