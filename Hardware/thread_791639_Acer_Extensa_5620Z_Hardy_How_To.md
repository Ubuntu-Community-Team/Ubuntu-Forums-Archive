---
title: "Acer Extensa 5620Z Hardy How To"
date: 2008-05-12
forum: Hardware
---

### Post by chrisby on 2008-05-12
Note: This post has been updated to configure under Hardy LTS Version 2:

1. Compiz works out of the box with the intel 965/X3100 graphics card
2.1. Broadcom 43 works by enabling the restricted STA driver (Requires Restart)
     System->Administration->Restricted Drivers
2.2.  Atheros wireless status?
3. no longer necessary

4. Hibernate and Suspend work out of the box, but resume after hibernate has no audio

This can be fixed by: 
4.1. Enabling "linux-backports-modules-hardy-generic" in synaptics.
4.2.    a. open the terminal
        b. ```
sudo gedit /etc/modprobe.d/alsa-base
```
        c. add "options snd-hda-intel model=acer" after the first line (thanks ScottNC)

5. Speakers may seem quiet. This can be fixed by:
5.1. open the terminal
5.2. run alsamixer
5.3  make sure that Master and PCM are up to 100

6. Audio input may appear not to work. If the volume control fails to yield any results:
6.1. open the terminal
6.2. run alsamixer
6.3  hit tab -> arrow to capture -> increase capture to 90%

For built in microphone set "Input So" to "Front Mi"
For microphone jack set "Input So" to "Mic"
I could not get the line in to work.


 
Notes on Intrepid and Jaunty:  

Intrepid has severe graphics performance degrades.
glxgears commands under hardy give approximately 900 FPS
glxgears commands under intrepid give approximately 300-500 FPS

Jaunty has improved graphics performance, but has random freezes associated with the intel chipset (Currently, the intel 965 is blacklisted and compositing wont work)

In my opinion, hardy is still the best (I wish I never left)

---

### Post by chrisby on 2008-07-05
Step 3 is no longer necessary

---

### Post by afewtips.com on 2008-08-05
Your wireless worked out of the box?

I did this and got it to work.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by chrisby on 2008-08-10
Yea, the card in the store had the Atheros wireless chipset, but mine came with a Broadcom 43xx wireless chipset (1 click in the hardware drivers tab).  Did you have the no sound after hibernate issue?

---

### Post by OprahDust on 2008-08-12
i tried installing Ubuntu 8.04 when i first got my 5620z a couple months ago, and i remember that most of everything worked out of the box for me, except for the delete key, which it looks like you fixed

but the major problem that i had was the microphone and front audio ports (line in, mic, headphones) weren't working

do either of you have the same problems? i would really like to give ubuntu another shot relatively soon before school starts up again

---

### Post by chrisby on 2008-08-12
I haven't had any issues with audio after applying step 4, and I use the headphone port all the time.  Maybe its an issue with pulse audio.  

My suggestion is to shrink your vista partition from within vista and try Ubuntu again on the free space.  If it doesn't work you can get back to vista without much headache (other than the headache of using vista :) ).  

The Delete key should work now without step three, and step four may fix your audio issues.

Ubuntu lists my sound device as a Realtek ALC268

Here is a screenshot of my sound preferences:

---

### Post by OprahDust on 2008-08-12
so, does the internal microphone work or not?

and by the way, i down(up)graded to XP from Vista, i just couldnt take it anymore

---

### Post by chrisby on 2008-08-12
I played around with it a little and couldn't get the internal microphone working.  The front line in, and microphone both worked though.

you should edit the down out of your last post, xp is an upgrade over vista :lolflag:.

---

### Post by jgor on 2008-09-16
Thanks for the help. I have an Extensa 5620 (no Z) and the sound fix works. I can now hibernate knowing that I can come back with sound. It should be noted though that a restart is required. For the complete Linux newbie gedit is a program for text and should be replaced with mousepad if you are using xubuntu. I took me a fair amount of time to figure this out since xubuntu is the only distribution I have tried so far.
I agree that vista is a terrible operating system. This is sad because I knew that vista sucked before I bought my acer Extensa 5620. The sad truth of the world we live in is that having windows makes a laptop cost less money; they already mass produce hardware windows-friendly, and they already mass produce support technicians windows-friendly. Speaking of which I'm going to need to find a good way of hiding my Linux partition because technically I voided my warranty on day one by installing xubuntu. The retailer actually told me I had to make (or keep) my hard drive windows-only or they won't fix any hardware.

---

### Post by cetheriel on 2008-10-04
just thought we should link (merge) these two topics.
[http://ubuntuforums.org/showthread.php?t=868841](http://ubuntuforums.org/showthread.php?t=868841)

---

### Post by chrisby on 2008-10-16
The Broadcom STA driver works much better than the cutter driver.:guitar:

---

### Post by chrisby on 2008-10-27
None of the above steps are necessary on Intrepid Ibex.:D

Sound works with no hibernation issues and the STA driver from broadcom works much better.

Progress is nice!

---

### Post by maet on 2008-10-28
how do i make my audio input or mic slot into a second audio out??

i DJ and i need main speakers out and an out going into my headphones...

---

### Post by chrisby on 2008-10-29
Is that possible? It may be easier to go to Radioshack and buy a splitter for a couple of bucks.

---

### Post by cetheriel on 2008-10-29
it is possible, yet i don't know how. it's not the same thing as an splitter, since you can send some audio on a channel and another output through the other channel...

---

### Post by zenith456 on 2008-11-24
Sometime about 2 weeks ago one of the ubuntu updates seems to have messed up my xorg. Xorg is constantly running at 25-35% on each core.

Has anyone else experienced this or have any suggestions for a fix? I'm on the verge of just doing a reinstall.

Running hardy upgraded to ibex, gnome, and recently disabled animations in AWN because it's getting so bad.

---

### Post by james.wilde on 2009-02-11
> **chrisby said:**
> None of the above steps are necessary on Intrepid Ibex.:D

Sound works with no hibernation issues and the STA driver from broadcom works much better.

Progress is nice!

Not sure I agree wholeheartedly with this, Chris.  I have a new - Nov 2008 - Acer Extensa 5620 with the HDA Intel soundcard.  I originally installed 8.10 and audio-video was hopeless.  In the end I reverted to 8.04, which had worked perfectly on my old works Dell and my old works HP.

8.04 works fairly well on the Acer, but I have the volume control open when making a Skype call so I can make sure the mike is working.  And another funny thing.  When I boot the machine, I hear the drum roll when the login screen comes up, and after login, I hear the first four or five notes of the login theme.  Then all is silent, and when I go into /System/Preferences/Sound, I hear nothing when I click on the login and logout sounds.  I have no idea why this is, and cannot find what it is that stops working during login.  All suggestions welcome.

Apart from that, I can play most CDs and videos, including Youtube, which I couldn't with 8.10.

Ubuntu is great, but imho audio-video is its weakest link, and in today's world, the thing that is going to sink it in competition with it's worst competitor.  I've had more hassle with AV on all versions than with all the rest of Ubuntu put together, including the fact that wireless almost never works out of the box (I seem to remember that it did, in fact, on this machine).

BTW, glad we have this 5620 thread.  One feels a little more confident knowing that commenters are using more or less the same kit.

//James

---

### Post by chrisby on 2009-04-22
@all

Jaunty audio seems to work better than Intrepid for me, but graphics have severely degraded.  The system is subject to random freezes.

[http://ubuntuforums.org/showthread.php?p=7122341#post7122341]("http://ubuntuforums.org/showthread.php?p=7122341#post7122341")

Also, if someone with an Atheros wireless can report on functionality or enabling on LTS 2 I will update the original post. 

@James, I vaguely remember the system doing that a long time ago with hardy, but I had been using intrepid and alphas of 9.04 for a while.  I just reinstalled with 8.04 LTS version 2 and I could hear the login and logout sounds on click. Sounds appear "on time" for me upon login or logout as well.  If I could duplicate it maybe I could help, but I am only a beginner/intermediate user.  

Did you install 8.04.2 LTS or 8.04.1 LTS?  Maybe a fresh install of 8.04.2 LTS would help.

---

### Post by jgor on 2009-05-24
Just wondering, will DVDs play for you on the Extensa 5620 with Ubuntu? When I run Vista (I dual boot through grub) I can watch DVDs just fine. But I don't think the manufacturer releases any Linux drivers. Therefore I just accept that if I use Linux on my laptop I will not get DVD playback, that is, until the Linux community improves whatever optical drive driver I am using now.

No one has mentioned DVD playback yet. Is that because it works on your Acer Extensas? It certainly doesn't on mine when I run Ubuntu.

---

### Post by cetheriel on 2009-06-04
in order to play dvds you've got to install libdvdcss2 from the medibuntu repository. just google for it. this is needed because the home video industry decided to encrypt every dvd in order to prevent them from being copied. needless to say, it doesn't work, just prevents happy customers from watching their crappy movies.
then you'd be better off by installing and using VLC. just go add/remove and search for it. it rocks and gives you access to menus and stuff.

---

### Post by jgor on 2009-06-04
> **cetheriel said:**
> in order to play dvds you've got to install libdvdcss2 from the medibuntu repository. just google for it. this is needed because the home video industry decided to encrypt every dvd in order to prevent them from being copied. needless to say, it doesn't work, just prevents happy customers from watching their crappy movies.
then you'd be better off by installing and using VLC. just go add/remove and search for it. it rocks and gives you access to menus and stuff.

Thanks. I would of thought that DVD playback would be easily found in the package manager.

I actually just installed Linux Mint and found that by default DVDs play just fine in it. Downloading and installing Linux Mint Elyssa was my way of going back to Hardy Heron, which, like others here found, works much better on the Extensa. What a confusing name though? I would have downloaded it much sooner if it were called Ubuntu Mint.

**[off topic]**
I read about the DVD encryption hack in Linus Torvalds' book. How funny that it was valid consumers that hacked the encryption so that they could watch purchased DVDs. The question now is will the Linux community have to do the same thing again for blu-ray disks? or was anything learned by these companies from this bit of history. All they have to do is make a decoder for Linux (like what Adobe did with flash) and the hack would come about much slower.
**[/off topic]**

---

### Post by cetheriel on 2009-06-04
well, most of the hardware support comes from the kernel, so going back to hardy shouldn't be any better. go figure. however, the reason ubuntu does not ship with the decoder but mint does, is that Canonical (responsible for ubuntu) is a service-provider corporation that wishes not to cross legal lines when it comes to intellectual properties, since Canonical offers comercial support for ubuntu. therefore, they do not ship those packages with ubuntu, although there is always medibuntu and other community packages. (this is the same reason why mp3 support does not ship in by default, although ubuntu-restricted-extras does the trick)
[offtopic]you know, those guys at the Industry know nothing of digital content. they did it again, on blue ray and HD-DVD and the code was broken again. let's just stay away from those draconian technologies an download DiVX right away, shall we?[/offtopic]

---

