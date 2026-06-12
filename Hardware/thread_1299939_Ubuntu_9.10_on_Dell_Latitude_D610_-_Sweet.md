---
title: "Ubuntu 9.10 on Dell Latitude D610 - Sweet"
date: 2009-10-24
forum: Hardware
---

### Post by dvfreelancer on 2009-10-24
Just got done upgrading my laptop from 9.04 to 9.1 and some basic testing.

Sweet. 

Running the online update is painless if a little slow, likely due to the load on their servers.  

It's an incremental update from 9.04 for sure, but it's really nicely done.  

No problems with sound or system settings.  It does seem to startup maybe a tiny bit slower, but operation seems overall faster.  

The new default look is very nice.  Seems a lot easier to read now and cleaner.  

Picked up all of my old network settings from 9.04 and connected to the wireless network without any intervention from me.  

Left my old desktop just like it was.  And I was surprised Gnome Do was still there and worked just fine.  

The new software center is a big improvement.  It loads much faster and the search is greatly improved.  Overall much cleaner.  Hopefully some day Canonical will develop it into an Apple-style app store and provide a way for developers to earn a little cash and to make some themselves.  

My first impression is that this update is a winner.  It's possible to take an older model like the D610 and get a totally usable, ready for business laptop.  It's better than it was new.  

I connect an external drive and use it to store video clips from my Canon 7D.  That camera and Ubuntu seem to get along just peachy. The data transfer rate is very fast and I can slam footage all day, up to the limit of my external storage and camera batteries.  

The only things on my wish list don't entirely depend on Canonical.  Tighter integration with GoogleDocs, Calendar and Gmail would be really nice.  A bonus if that included Picasso, Flickr, Facebook, Vimeo and YouTube.  

It found my network printer without any problems and setup was a breeze, though the local network tools are still a little obtuse.  

Overall, a nice step forward for Canonical that shows how Ubuntu can really shine.  Good job, y'all.  \\:D/

---

### Post by seamustry on 2009-11-03
thanks...i also have d610 and will go ahead and upgrade

---

### Post by RgnKjnVA on 2009-11-03
D610 owner here, thanks for posting your experience. I'm going to make sure my nightly backup worked and dive in. I'm kinda bored with my laptop. heh heh Couple questions if you don't mind.

Have you happened to have tried bluetooth on KK via a dongle?
Can you set your resolution higher than 1024?

---

### Post by dvfreelancer on 2009-11-03
> Have you happened to have tried bluetooth on KK via a dongle?
Can you set your resolution higher than 1024? 

No on both, unfortunately.  

Are those things you can test on a live install?

---

### Post by bagpussnz on 2009-11-04
Hi,
Does your internal microphone work. Damned if I can get mine to work.

Cheers,
Ian

---

### Post by RgnKjnVA on 2009-11-04
D610s have an internal mic?

dvfreelancer, good point re: live CD to check those items I asked about.

---

### Post by dvfreelancer on 2009-11-04
I didn't know I had an internal mic.

---

### Post by dvfreelancer on 2009-11-04
I don't have an internal mic.

[http://en.community.dell.com/forums/t/17126412.aspx]("http://en.community.dell.com/forums/t/17126412.aspx")

---

### Post by mab494 on 2009-11-04
I don't appear to be having the same luck as the rest of you.  Network reports connected but will not download anything.  Wireless network doesn't work at all.  Didn't actually upgrade from 9.04 - just nuked XP off it with a clean install :o(

---

### Post by dvfreelancer on 2009-11-04
Did you download your iso and burn a disk?  Did you test it with the live version first?  

If you burned the iso consider the possibility of a corrupt disk image.  That's happened to me more than once.  

Or you can try the 9.04 upgrade route.

---

### Post by mab494 on 2009-11-04
Yup, did the disk test.  First 2 had file errors so redownloaded and get an iso with no reported errors.  Install was easy and quick - just now have OS with no connectivity.

---

### Post by dvfreelancer on 2009-11-04
Since you did the disk check I assume you also entered your connection strings properly.  

I can connect anywhere with mine and it remembers them all.  Office, home, fire station...once I set them, it remembers.

---

### Post by mab494 on 2009-11-04
Thanks for the help.  i am pretty sure I entered everything correctly (both installs), but not happy ubuntu D610.  The solaris 6400 has no issues like this - ;-)

---

### Post by bagpussnz on 2009-11-04
Sorry - just made the assumption it had one. I guess that explains why it doesn't work then.
:-)

---

### Post by mab494 on 2009-11-04
If anyone has issues with the D610 and wireless from a 9.10 clean install - try;-
 
sudo apt-get install bcmwl-kernel-source
 
Then System --> Administration --> Hardware Drivers and install the broadcom driver that is there.  I now am connected to the internet wirelessly.

---

### Post by seamustry on 2009-11-08
i'm having problems with the headphone and speaker volume control: i can't get both volumes to go up and down at the same time. only main speaker volume goes up. headphone volume stays at loudest setting unless i change it in alsamixer in terminal.

---

### Post by tomverweij on 2010-02-23
Hi all,

Writing this on a D610 with a brandnew Karmic, from ISO CD, replacing XP.
Really happy with it ! :D

Most stuff worked fine (even Wireless), except:

- touchpad/mouse went crazy at random moments;
Seemed known issue, fixed by de-activating pointing stick, used some googled thread to fix that (i might look it up again if requested)

- currently experienced several times that screen goes crazy with all kinds of colorblocks, mostly bright pink. Really weird to watch :confused:. Restart usually fixes it, however tonight it was different: first screen went black & white and the system then froze. Two restarts did not fix it, third one did.

Anybody seen this before ?

Cheers
Tom

---

### Post by fredthomke on 2010-02-26
I'm about to install 9.10 on a Latitude D830. I don't expect it will be all that different than a D610. In fact, I previously had 9.04 on this laptop (part of a dual-boot with XP), but I completely trashed the drive and had to replace it (long story).
 
Anyway, I'll report back with my results. I will likely have to apt-get the broadcom stuff for my WiFi, I'm not sure. Of course, I'll do the Live-CD first, and poke around a bit, before actually installing.
 
As I recall, I had VERY good luck with the 9.04 and my video set to 1280x800. I'm pretty sure I could have gone all the way to 1920x1200, but my poor eyes don't like such tiny pixels. At 1280x800 it looked great.
 
Stay tuned!
- - fred
 
PS -- please do send me the links to disable the pointing stick, it just gets in my way.

---

### Post by fredthomke on 2010-02-27
OK, install went AWESOME! Had some minor quibbles with nVidia setup not wanting to write to xorg.conf, but some searching in this forum showed the solution.  Other than that, almost EVERYTHING was plug n' play.  Even Wifi drivers went in (as proprietary drivers, but painlessly) again point, click, and installed.

My laptop is now TRI-boot: XP, Vista, and now Ubuntu!!

Woo-hoo!!

- - fred

---

### Post by TnJ on 2010-03-21
> **seamustry said:**
> i'm having problems with the headphone and speaker volume control: i can't get both volumes to go up and down at the same time. only main speaker volume goes up. headphone volume stays at loudest setting unless i change it in alsamixer in terminal.


Same exact problem here.

---

### Post by tomverweij on 2010-04-07
Hi,

Couple of post earlier I offered to supply the googled link to switch of the Dualpoint Stick on my Dell.

Here it is: [http://pythoneering.blogspot.com/2009_11_01_archive.html](http://pythoneering.blogspot.com/2009_11_01_archive.html)

Creating this /etc/hal/fdi/preprobe/disable.fdi file with content worked form me:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
    <match key="input.product" string='DualPoint Stick'>
        <merge key="info.ignore" type="bool">true</merge>
    </match>
</device>
</deviceinfo>


Ok, and now for something completely different:
DVD playback is rather noisy. Issueing 'sudo hdparm -y /dev/cdrom' spins down the drive, but soon enough it goes BZZZZ really loud again.
And then sometimes the system decides to spin down again. Is there a way to permanently control this ? E.g. when watching a DVD, force a low speed ?

I tried 'eject -X <speed> /dev/cdrom' as well, no effect.

I'm curious....

Regards
Tom

---

### Post by tomverweij on 2010-07-30
hi, me again.

After upgrading to Lucid the drifting mouse problem has reappeared.
# sigh #

So somehow the disable.fdi file trick is not working at the moment.
While I'm searching maybe someone can but in and help out....

Anybody ?


cheers
Tom](*,)

---

### Post by dvfreelancer on 2010-07-30
Can you describe the touchpad problem in more detail?  Mine seemed to jump around a lot at first, then I realized that the right side of the touchpad is set up for scrolling (or zooming on Google maps).  

If I stay on the left side of the pad, no problems.  It's only the right quarter that makes it jump around.

---

### Post by tomverweij on 2010-07-31
Hi,

Thanks for your reply.
It's completely irratic. Sometimes it's even gone for hours. And then it kicks again, and persisting after a restart. But this phenomena is not new, according to several links.
What IS painfull is that I had it fixed under 9.10 and now it's back again under 10.4.
I tried to figure out if the hal-devices output somehow is different causing the disable.fdi file not to disable the stick. But no differences show.

Where to look now ?

Regards
Tom

---

### Post by tomverweij on 2010-07-31
Hi, 

me again on the drifting mouse issue.
It turns out that 'hal' is not active in 10.4 anymore.
I now need to disable the Dualpoint Stick using 'udev'
The manual pages give me a hard time.

Anybody able to guide me with a couple of steps ?
I will keep on looking myself so eventually will post the solution, but a shortcut might save me time :-)

Tom

---

### Post by tomverweij on 2010-08-01
Good news ! :popcorn:

Found a simpler way to get rid of the DualPoint Stick.
Look here: [http://cederlys.wordpress.com/2010/07/13/disabling-the-track-stick-in-ubuntu/#comment-4](http://cederlys.wordpress.com/2010/07/13/disabling-the-track-stick-in-ubuntu/#comment-4)

It's: 
```
$ xinput -set-prop "DualPoint Stick" "Device Enabled" 0
```

I stuck it into a startup app and my problems seem over.

Regards !
Tom

---

