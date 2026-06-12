---
title: "Fixed Headphones + Speakers issue on LG R700 laptop"
date: 2008-07-26
forum: Hardware
---

### Post by Ramaddan on 2008-07-26
I recently tried installing Ubuntu Hardy 8.04 (32-bit) on an LG R700 laptop, and was glad that most things worked out of the box without much tweaking.

Only two things did not work correctly: the sleep/hibernate function, and the headphones would work at the same time as the speakers.

I did not resolve the sleep/hibernate issue, but I finally figured out the headphones and speakers issue.

I had to do lots of searching and testing for this, and finally succeeded, thanks to God.

The issue I had was that the headphones and speakers would be on at the same time, and whenever I turned OFF the headphones, the speakers would turn OFF, and vice versa.

And consequentially, the laptop would not detect the headphones and would therefore not re-route the sound from the speakers to the headphones.

Here are the steps I took to fix my annoying issue.

Keep in mind that this was done for an LG R700 laptop, but it might be useful to others.


Run the following to get what codec is being used:

> head -n 1 /proc/asound/card0/codec*

And you should get something like:

> Codec: Realtek ALC888


Then run the following to read the model options under your card model, in my case ALC888, which was under ALC883/888:

> zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

Or you can alternatively read the following link for the options:
> [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)


I tried a lot of options (while not caring much for SPDIF), and the two following options worked for me with this card and laptop combination:

> 3stack-6ch
targa-2ch-dig

I added the option I chose to the alsa options file by doing the following:

> gksu gedit /etc/modprobe.d/alsa-base

I changed the following line:

> options snd-hda-intel position_fix=1 model=ref

To:

> options snd-hda-intel position_fix=1 model=targa-2ch-dig

Close file and **restart computer** for changes to take effect.


**_Conclusion:_**

The reasons as to why I stuck with the option "targa-2ch-dig" as opposed to "3stack-6ch" was due to three reasons:

1) My laptop only had 2.1 channels and not six channels and did not know of the consequences that could arise
2) Even though the six channels worked in the short period I tested it, it did not automatically turn off the speakers when I plugged in the headphones
3) A side quirk that also came with the six channels option was that I had to turn OFF instead of ON the headphones switch in order to have sound on the headphones

All in all, the "targa-2ch-dig" works well with me (even though I did not try all options), and it now automatically detects when the headphones are plugged or not, and routes the sound accordingly.

I am no expert, so please don't expect any technical feedback from me. I just kept hammering till it worked.

Now everything works on this laptop, except for the sleep and hibernate function.

**Note: Make sure that the "Headphones" switch is turned ON for the "targa-2ch-dig" option in order for the headphones to be detected.**

---

### Post by levidos on 2008-12-14
thanks for the post.

did you find any solution for the hibernation/stand by problem?

---

### Post by Ramaddan on 2008-12-14
Hi,

Unfortunately not really, but I found a work around which at least works in terms of hibernation for both suspend and hibernate and does not crash on the LG R700.

I took it either from this thread:
[http://jrobbo.com/blog/?tag=ubuntu-hibernate-suspend-uswsusp]("http://jrobbo.com/blog/?tag=ubuntu-hibernate-suspend-uswsusp")

Or at least one with a similar solution.

I wish I could get the in-built suspend and hibernate to work though, as it would be a more elegant solution.

Hope it helps.

---

### Post by denisius on 2009-02-09
> **Ramaddan said:**
> Hi,

Unfortunately not really, but I found a work around which at least works 
I wish I could get the in-built suspend and hibernate to work though, as it would be a more elegant solution.

Hope it helps.

Hello. I have the same laptop LG R700, and I really so glad, that there are people who have the same laptop :) Together we will win!

Do you mean that this solution can do hibernate working, but not suspend?

I've created bug in kernel's bugzilla about wrong suspend: [http://bugzilla.kernel.org/show_bug.cgi?id=11255](http://bugzilla.kernel.org/show_bug.cgi?id=11255)

also I create the same report in Ubunta bugzilla, but there  isn't any comment...

As for speakers I have problem - I cannot hear anything from sub-woofer, and also what about buttons like dolby, and camera?

So, Any answers will be appreciated:)

---

### Post by Ramaddan on 2009-02-10
Hi Denisius,

1) I used the following to assign the dolby and camera key.

[http://xpd259.blogspot.com/2008/10/gnome-keybindings-on-linux.html]("http://xpd259.blogspot.com/2008/10/gnome-keybindings-on-linux.html")

You might need to log out and in.

Instead of using the keys alt+ctrl+X, I used instead:
> **XF86WebCam** for the webcam key
**XF86Launch1** for the Dolby Key

I assigned the XF86WebCam key to _**cheese**_ as the command to run.

As for XF86Launch1, I just assigned it to run something else, as I had no idea of how to implement this dolby feature in Linux.

You can also use the following to assign a few things instead as well:
> System->Preferences->Keyboard Shortcuts

2) For the hibernation issue, I used the following instead:
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

Which is really not an elegant fix, but rather a quick hack, which can be overridden by updates at some point.

3) So all in all, at least my laptop does not crash when I choose sleep or hibernate, and the webcam key works properly, and the dolby key does something as opposed to being useless.

Hope this is useful in any way.

EXTRA
=====
Since you have the same laptop as me, you might have noticed a decrease in battery time maybe, for which I did the following to increase battery time.

Do the following in a terminal:
> sudo apt-get install cpufrequtils

Then set as follows:> 
sudo cpufreq-set -c 0 -g ondemand
sudo cpufreq-set -c 1 -g ondemand

You can do the following to see processors info:
> sudo cpufreq-info

This seems to handle the Intel Processor Frequencies better, and change them as appropriate.

I have no idea why it is not default when the system detects processor type.

**This needs a restart.**

I also did the following, but you might not want it:
> sudo hal-disable-polling --device /dev/cdrom

This disables the constant polling of CD-Drive by HAL, which helps with battery life.

To re-enable it:
> sudo hal-disable-polling --enable-polling --device /dev/cdrom

Hope this helps your battery life.

**Last note:** My bass works after I did the steps in the first post of this thread, so I don't know why yours does not. Did you check Volume Control?

---

### Post by Ramaddan on 2009-02-16
Hi Denisius,

I realized that I did not mention an important step.

I had to use the KeyTouch program in order to get the keys of the laptop to be recognized.

I installed the program from this repo, which you can add into software sources:
> [http://ppa.launchpad.net/nick-colgan/ubuntu](http://ppa.launchpad.net/nick-colgan/ubuntu)

Type the following in a terminal after adding sources and updating repos:
> sudo apt-get install keytouch keytouch-editor

You might need to restart for KeyTouch to initiate before setting it up.

You need to first setup your laptop keyboard with KeyTouch editor, then import it into KeyTouch.

After that is done, then your laptop keys **XF86WebCam** and **XF86Launch1** will be recognized.

Hope this helps.

---

