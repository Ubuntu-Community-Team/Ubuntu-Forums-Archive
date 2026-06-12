---
title: "Ubuntu 11.04 - No sound at all"
date: 2011-04-30
forum: Hardware
---

### Post by Joeferson on 2011-04-30
Hi, I am new to ubuntu and linux. I have just installed ubuntu 11.04 on my lap top (a Itautec infoway n8610 ss) and it works perfectly... except for the sound. I can´t get any sound from my pc, it worked well with my windows vista but it is not working now. I tried to find the driver for the on-board soundcard to, maybe, replace it, but I can't even find it. The sound is not mute, I tried different programs (mp3 players, Internet flash based sites), I used the test function on the sound preferences and nothing. What should I do? It is my final frontier to finally be a linux user...

---

### Post by psilogon on 2011-04-30
**Try to determine the make of your sound card**

Run the following command in a terminal: 

```
aplay -l | grep card
``` This will probe your system, filtering lines that include the string 'card'. If you get results when you run this, you should be able to tell what make your sound card is. My results look like:

```
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
card 1: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
```

If you have an Intel card, one thing that worked for me in the past is this: [http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html]("http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html")

Finally, if you run the command

```
sudo lsmod | grep snd
```

and see results that look similar to this:

```
snd_hda_intel          24140  4 
snd_hda_codec          90901  1 snd_hda_intel
snd_emu10k1_synth      12964  0 
snd_emux_synth         33506  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13482  1 snd_emux_synth
snd_emu10k1           137068  5 snd_emu10k1_synth
snd_ac97_codec        105614  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  6 snd_hda_intel,snd_hda_codec,snd_emu10k1,snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13274  3 snd_hda_codec,snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51291  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14110  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  26 snd_hda_intel,snd_hda_codec,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_hda_intel,snd_emu10k1,snd_pcm

```

then most likely you're not in for too much of a headache.

**Unmuting**

Also, if you have multiple cards, try going to "Sound Preferences", selecting the "Output" tab, and toggling between your various options.

You could also try downloading a mixer, like Gnome Mixer, and manually unmuting things. Try different applications.

---

### Post by lidex on 2011-04-30
This should get you started:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Joeferson on 2011-05-01
Thank you, guys. Problem solved. I can finally rest at peace now... an listen to music!
I am really grateful to the ubuntu community, for providing the system and helping beginners like myself to get started. Bye!

---

### Post by lidex on 2011-05-01
Once you sure audio works please mark this thread solved using 'Thread Tools' up top.;-)

---

### Post by Joeferson on 2011-05-01
Done.
And thanks again!

---

### Post by RoscoPeco on 2011-05-03
What exatly was done to solve your issue? I have a similar issue since upgradeing to 11.04, sound has worked fine on all previous versions.  Here is the link to my ALSA info [http://www.alsa-project.org/db/?f=16256bda1097c391b7fa67ed5a4a961dfb370a1b](http://www.alsa-project.org/db/?f=16256bda1097c391b7fa67ed5a4a961dfb370a1b)

---

### Post by lidex on 2011-05-03
> **RoscoPeco said:**
> What exatly was done to solve your issue? I have a similar issue since upgradeing to 11.04, sound has worked fine on all previous versions.  Here is the link to my ALSA info [http://www.alsa-project.org/db/?f=16256bda1097c391b7fa67ed5a4a961dfb370a1b](http://www.alsa-project.org/db/?f=16256bda1097c391b7fa67ed5a4a961dfb370a1b)

I would imagine the troubleshooting link I posted led him there.
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by joel.benavidez on 2011-05-05
Lidex, I ran through all the preliminaries and code and nada. Then I tried  your link. It spit this report at me. I'm guessing it's the insight needed to correct this issue?

[http://www.alsa-project.org/db/?f=fdb9c7bed67896aaa082327ce992a25a3b655213]("http://www.alsa-project.org/db/?f=fdb9c7bed67896aaa082327ce992a25a3b655213")

 I'm having all the same symptoms. Any help is greatly appreciated.

Ah, and I'm equally green when it comes to linux, though I am trying hard. :/

---

### Post by lidex on 2011-05-06
> **joel.benavidez said:**
> Lidex, I ran through all the preliminaries and code and nada. Then I tried  your link. It spit this report at me. I'm guessing it's the insight needed to correct this issue?

[http://www.alsa-project.org/db/?f=fdb9c7bed67896aaa082327ce992a25a3b655213]("http://www.alsa-project.org/db/?f=fdb9c7bed67896aaa082327ce992a25a3b655213")

 I'm having all the same symptoms. Any help is greatly appreciated.

Ah, and I'm equally green when it comes to linux, though I am trying hard. :/
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Joeferson on 2011-05-06
I see a lot of people have the same problems I had. Well, I must say my problem was really simple. I just had to unmute one of the itens in my soundcard driver config menu. The important thing for me was to learn how to open this menu, which I did by accessing the terminal application and typing "alsamixer".
By the way the wiki guide lidex suggested me was of invaluable help. That really did the trick.

---

### Post by joel.benavidez on 2011-05-14
This is what I got:

```
joelbenavidez@joelbenavidez-Satellite-M115:~$ echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for joelbenavidez: 
options snd-hda-intel model=auto
joelbenavidez@joelbenavidez-Satellite-M115:~$ 

```

After the reboot, it accomplished nothing. I thought that it could have been my speakers going bad or something, so i reloaded 10.04 netbook. My sound worked fine. I just loaded 11.04 again and tried the code once again. Still nothing on 11.04. I may just switch over to LTS or try Ubuntu Studio until this version gets a bit more stable.

---

### Post by ps2k on 2011-05-14
I have recently upgraded my system to 11.04. Sound worked perfectly over a week. It just stopped working today. I tried re-installing alsa sound utils, and pulse audio. In fact the audio icon has gone missing in the top right side of the status bar.
In any case here is the output of the script. Could somebody please help me in getting my audio work properly?
[http://www.alsa-project.org/db/?f=d06bd6bba5e13fa98ff92ded35186a50c690b7f0](http://www.alsa-project.org/db/?f=d06bd6bba5e13fa98ff92ded35186a50c690b7f0)

---

### Post by demilord on 2011-05-14
Check the sound preferences, sometimes its set on HDMI on default and is output muted.

---

### Post by araidian on 2011-05-14
hey guys i know this post is resolved but i thought i would add that i to has this issue, and i resolved it by opening users and groups in unity and clicking groups and double clicking on audio, pulse, and pulse access, and putting a tick in they're tick boxes .. respectively.

it seems that for what ever reason the user account didnt enable access to that group ergo the user didnt have permission to access the resource.  i hope this helps someone out if not i'm sure it will save me time later when this happends again and i have to google it :)

peace.

---

### Post by lidex on 2011-05-14
> **joel.benavidez said:**
> This is what I got:

```
joelbenavidez@joelbenavidez-Satellite-M115:~$ echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for joelbenavidez: 
options snd-hda-intel model=auto
joelbenavidez@joelbenavidez-Satellite-M115:~$ 

```

After the reboot, it accomplished nothing. I thought that it could have been my speakers going bad or something, so i reloaded 10.04 netbook. My sound worked fine. I just loaded 11.04 again and tried the code once again. Still nothing on 11.04. I may just switch over to LTS or try Ubuntu Studio until this version gets a bit more stable.

Try 3stack or 3stack-dig instead of auto.
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by ps2k on 2011-05-14
Thanks for the replies.
As demilord suggested I checked sound output. It is not muted. Then I followed aradian's instructions of checking the groups. Although audio was checked, pulse and pulse-access were not. I selected those two but not sound even after reboot.
Any other thoughts on this?

---

### Post by ps2k on 2011-05-14
Now my sound seems to be working fine. After pressing mute button on my laptop now it is working. But I'm pretty sure that mute and volume up and down buttons of my laptop never worked for me before. Thanks a lot.

---

### Post by thxq on 2011-05-15
> **lidex said:**
> I would imagine the troubleshooting link I posted led him there.
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**
* Ignore any 'No such file or directory' errors*
U know what ,U helped me get thru ...
thank a million:popcorn:

---

### Post by buntus00 on 2011-06-05
I had the same problem. I followed the scripts and then went to the alsa site, and pored over the output, and said: What am I supposed to do with all this info?  How does that solve my problem. All this complication.

I solved this by following the simple stuff.  System > Preferences .Sound.   I unmuted the volume which is apparently defaulted to that, which is understandable really, as many people who have sound cards in their computers would prefer them not to work by default and cause them tumultuous hair-pulling and head-banging for every good reason. Hats off to Ubuntu for recognizing this. 

But it's the simple stuff that gets you every time. 

When all's said and done, it's a very pretty OS though, and nicely designed.

---

### Post by lidex on 2011-06-05
> **buntus00 said:**
> I had the same problem. I followed the scripts and then went to the alsa site, and pored over the output, and said: What am I supposed to do with all this info?  How does that solve my problem. All this complication.

I solved this by following the simple stuff.  System > Preferences .Sound.   I unmuted the volume which is apparently defaulted to that, which is understandable really, as many people who have sound cards in their computers would prefer them not to work by default and cause them tumultuous hair-pulling and head-banging for every good reason. Hats off to Ubuntu for recognizing this. 

But it's the simple stuff that gets you every time. 

When all's said and done, it's a very pretty OS though, and nicely designed.

There is more than one guide available that goes over the basics such as muted levels, etc. That should be the first place anyone should look.

---

### Post by Karolkens on 2011-06-13
I also don't have sound in my Ubuntu 11.04. Could you look at my log? [http://www.alsa-project.org/db/?f=ae8eb85baea8f7a7bc784339f44cff2bbe6b2907]("http://www.alsa-project.org/db/?f=ae8eb85baea8f7a7bc784339f44cff2bbe6b2907")

---

### Post by Yellow Pasque on 2011-06-13
> **Karolkens said:**
> I also don't have sound in my Ubuntu 11.04. Could you look at my log? [http://www.alsa-project.org/db/?f=ae8eb85baea8f7a7bc784339f44cff2bbe6b2907]("http://www.alsa-project.org/db/?f=ae8eb85baea8f7a7bc784339f44cff2bbe6b2907")
I looked at it and didn't see anything glaringly wrong. Double check the volume is not muted in alsamixer:
```
alsamixer
```
As a last resort, you can try upgrading ALSA manually: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by lidex on 2011-06-13
Try a suspend/resume cycle:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498)

---

### Post by sanjeevpunj on 2011-06-15
> **psilogon said:**
> **Try to determine the make of your sound card**

Run the following command in a terminal: 

```
aplay -l | grep card
``` This will probe your system, filtering lines that include the string 'card'. If you get results when you run this, you should be able to tell what make your sound card is. My results look like:

```
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
card 1: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
```

If you have an Intel card, one thing that worked for me in the past is this: [http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html]("http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html")

Finally, if you run the command

```
sudo lsmod | grep snd
```

and see results that look similar to this:

```
snd_hda_intel          24140  4 
snd_hda_codec          90901  1 snd_hda_intel
snd_emu10k1_synth      12964  0 
snd_emux_synth         33506  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13482  1 snd_emux_synth
snd_emu10k1           137068  5 snd_emu10k1_synth
snd_ac97_codec        105614  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  6 snd_hda_intel,snd_hda_codec,snd_emu10k1,snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13274  3 snd_hda_codec,snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51291  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14110  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  26 snd_hda_intel,snd_hda_codec,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_hda_intel,snd_emu10k1,snd_pcm

```

then most likely you're not in for too much of a headache.

**Unmuting**

Also, if you have multiple cards, try going to "Sound Preferences", selecting the "Output" tab, and toggling between your various options.

You could also try downloading a mixer, like Gnome Mixer, and manually unmuting things. Try different applications.

I had this situation,still have it,although sound plays through my default inbuilt sound card, it doesn't play through my second sound card installed on the PCI slot. Nor do I get to open the SOUND PREFERENCES window when I click the speaker icon at the top right, so I cannot choose the output to play through my chosen card! Anyway still hammering at my keyboard, to find an answer.

---

### Post by brandon.thies on 2011-06-15
Hello All, 

This is my first post on the Ubuntu forum! I recently installed Ubuntu 11.04 on my computer but I can't seem to get the sound to work. I've tried what little I can do but with no success. 

 Here is  more details via a ASLA Information Script LSA Information Script 

[URL="http://www.alsa-project.org/db/?f=6f4170b85964558ad0da5dcb6053f39882454eb4"]http://www.alsa-project.org/db/?f=6f4170b85964558ad0da5dcb6

Any help would be greatly appreciated053f39882454eb4[/URL]!

---

### Post by lidex on 2011-06-15
> **brandon.thies said:**
> Hello All, 

This is my first post on the Ubuntu forum! I recently installed Ubuntu 11.04 on my computer but I can't seem to get the sound to work. I've tried what little I can do but with no success. 

 Here is  more details via a ASLA Information Script LSA Information Script 

[URL="http://www.alsa-project.org/db/?f=6f4170b85964558ad0da5dcb6053f39882454eb4"]http://www.alsa-project.org/db/?f=6f4170b85964558ad0da5dcb6

Any help would be greatly appreciated053f39882454eb4[/URL]!

You may want to update your bios. In the meantime try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by brandon.thies on 2011-06-15
Thanks Lidex! I updated the bios and now the sound works perfectly!

> **lidex said:**
> You may want to update your bios. In the meantime try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by kira0030 on 2011-06-18
> **lidex said:**
> This should get you started:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Could someone please help me sort out my sound problem.

I went through the debugging page suggested above but still no sound.
Here is the link to my alsa output.
[http://www.alsa-project.org/db/?f=4ee54b8e6509f5e8469693ae2f3a575ab78b1a6a](http://www.alsa-project.org/db/?f=4ee54b8e6509f5e8469693ae2f3a575ab78b1a6a)

Thanks, Kylie

---

### Post by lidex on 2011-06-18
> **kira0030 said:**
> Could someone please help me sort out my sound problem.

I went through the debugging page suggested above but still no sound.
Here is the link to my alsa output.
[http://www.alsa-project.org/db/?f=4ee54b8e6509f5e8469693ae2f3a575ab78b1a6a](http://www.alsa-project.org/db/?f=4ee54b8e6509f5e8469693ae2f3a575ab78b1a6a)

Thanks, Kylie
Pretty old install. You would be better served, I believe, installing a newer version of ubuntu.

---

### Post by wfoster on 2011-06-18
Having a similar problem. Upgraded to 11.04. Sound worked for a while then quit. I'm basically a noob so any help would be appreciated. 

[http://www.alsa-project.org/db/?f=bde70e6e6f0c7a91d648f255928f35827d01a76f](http://www.alsa-project.org/db/?f=bde70e6e6f0c7a91d648f255928f35827d01a76f)

---

### Post by Yellow Pasque on 2011-06-18
> **wfoster said:**
> Having a similar problem. Upgraded to 11.04. Sound worked for a while then quit. I'm basically a noob so any help would be appreciated. 

[http://www.alsa-project.org/db/?f=bde70e6e6f0c7a91d648f255928f35827d01a76f](http://www.alsa-project.org/db/?f=bde70e6e6f0c7a91d648f255928f35827d01a76f)
Try resetting your pulse user files and logging out/in:
```
rm -rf ~/.pulse*
```
If that doesn't help, please start a new thread. This one's getting confusing as a lot of people are posting help requests in a thread marked 'solved'.

---

### Post by kira0030 on 2011-06-19
> **lidex said:**
> Pretty old install. You would be better served, I believe, installing a newer version of ubuntu.

I'm stuck with 8.04 at the moment, need to borrow sister's external hard drive to do complete back up.  :-)

I'm also using win4lin which afaik only works with Ubuntu up to 9.04.  Will wait until I upgrade as you say hopefully that will fix it.

Thanks :p

---

### Post by kromazone on 2011-06-24
when I ran the command to see my cards I got 
card 0: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
card 0: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
To me the 1st 2 look to be conflicting. Am I right at this assumption and if how can I fix it?

---

### Post by DimasRobin on 2011-06-25
Hi. I am new to Ubuntu and I am familiarizing with the system.
Like many users I have no sound and I could use some detailed help to solve my issue.

Here is a link to my: [http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a](http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a)

Thank you again for your help. :)

---

### Post by Yellow Pasque on 2011-06-25
> **DimasRobin said:**
> Hi. I am new to Ubuntu and I am familiarizing with the system.
Like many users I have no sound and I could use some detailed help to solve my issue.

Here is a link to my: [http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a](http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a)

Thank you again for your help. :)
I don't know if it will help, but you are running an old BIOS, and there have been several updates, including an update the the southbridge code: [http://www.msi.com/product/mb/H55M-E33.html#/?div=Download](http://www.msi.com/product/mb/H55M-E33.html#/?div=Download)

I didn't see anything obviously wrong in your info.

---

### Post by Yellow Pasque on 2011-06-25
> **kromazone said:**
> when I ran the command to see my cards I got 
card 0: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
card 0: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
To me the 1st 2 look to be conflicting. Am I right at this assumption and if how can I fix it?
No, you have analog output and digital output, like many sound cards. Post your alsa-info: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by lidex on 2011-06-26
> **DimasRobin said:**
> Hi. I am new to Ubuntu and I am familiarizing with the system.
Like many users I have no sound and I could use some detailed help to solve my issue.

Here is a link to my: [http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a](http://www.alsa-project.org/db/?f=5f323a103ed6dd0b25ff51e0ee6cad35344be69a)

Thank you again for your help. :)

Your dmesg shows your model selection in alsa-base.conf is not correct. What are these outputs please:
```
cat /etc/modprobe.d/alsa-base.conf
ls /etc/modprobe.d/
```

Are you trying to get hdmi or analog output?

---

### Post by pithnub on 2011-07-01
The thread says solved, but I just wanted to give my experience with the same problem, having upgraded to 11.04 yesterday from 10.10 Desktop. 
I am unfamiliar still with the layout of 11.04, and could not see a terminal link anywhere. No problem, just look in the Ubuntu help, and the answer was there. It pointed me to search for "sound", which brings up two options, one of which is simply...sound. Opening this showed the correct device was chosen, but it was automatically muted - for some bizarre, who knows why reason. 
Another point. I dual boot this pc, with XP Pro, which at least recognises my MP250 Canon printer, and does a few other things I like. Now, on boot-up, the screen blanks at the OS selection page, due to the display being out of frequency for my monitor. XP is always the bottom option on this selection page, so I just scroll down (blind!) and press enter to get XP going, otherwise, I just hang around until 11.04 decides to auto boot. Is 11.04 an improvement?...We;;, its not actually any worse..ish....

---

### Post by Yellow Pasque on 2011-07-01
> **pithnub said:**
> The thread says solved, but I just wanted to give my experience with the same problem, having upgraded to 11.04 yesterday from 10.10 Desktop. 
I am unfamiliar still with the layout of 11.04, and could not see a terminal link anywhere. No problem, just look in the Ubuntu help, and the answer was there. It pointed me to search for "sound", which brings up two options, one of which is simply...sound. Opening this showed the correct device was chosen, but it was automatically muted - for some bizarre, who knows why reason. 
Another point. I dual boot this pc, with XP Pro, which at least recognises my MP250 Canon printer, and does a few other things I like. Now, on boot-up, the screen blanks at the OS selection page, due to the display being out of frequency for my monitor. XP is always the bottom option on this selection page, so I just scroll down (blind!) and press enter to get XP going, otherwise, I just hang around until 11.04 decides to auto boot. Is 11.04 an improvement?...We;;, its not actually any worse..ish....
Huh? Are you having an issue? Are you a bot or troll? Make another thread if you're seriously seeking technical support..

---

### Post by pithnub on 2011-07-02
Sorry to disappoint you in your search for trolls but I'm a mere human. I do have other Ubuntu 11.04 issues, and felt the conversational style of a forum was a reasonable place to mention this without implying I needed anyone's help. The main reason for posting was simply to provide another solution to the no sound problem based on my own experience today (i.e. look in the Ubuntu help first). Sorry if that's a distraction from all this techno-babble you guys are banging on about. Geez! 
Sorry if my off-the-cuff comments about the experience of upgrading to 11.04 seemed like a trawl, but let's not kid ourselves that this latest version is as easy to navigate and as straightforward as 10.10. I wonder why I bother..

---

### Post by Yellow Pasque on 2011-07-02
> **pithnub said:**
> Sorry to disappoint you in your search for trolls but I'm a mere human. I do have other Ubuntu 11.04 issues, and felt the conversational style of a forum was a reasonable place to mention this without implying I needed anyone's help.
No. This isn't the place to shoot the ***** about your opinion of whether this Ubuntu version is better than that Ubuntu version. See the community cafe for that kind of pointless drivel.

---

### Post by dom1n1cus on 2011-07-02
Hello.
I have the same problem. I just installed Ubuntu and sound doesn't work. Nothing I've tried seems to get it working.
Here is the Alsa info: [http://www.alsa-project.org/db/?f=962a527fd8d6b474bff25a9637a8df10d17631fa](http://www.alsa-project.org/db/?f=962a527fd8d6b474bff25a9637a8df10d17631fa)
Thank you for any piece of advice.

edit: Problem solved. Please don't ask. I feel to embarrassed. ;)

---

### Post by buckadilla on 2011-07-02
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**
* Ignore any 'No such file or directory' errors*[/QUOTE]


Right as rain. Thank you so much!

---

### Post by pithnub on 2011-07-03
> **Temüjin said:**
> No. This isn't the place to shoot the ***** about your opinion of whether this Ubuntu version is better than that Ubuntu version. See the community cafe for that kind of pointless drivel.

Thanks for putting me straight. Still, I did manage to fix this problem without all the technical CLI stuff you're talking about, and still wonder why 11.04 defaulted to mute on upgrade? Seems like a bug to me, or is that more mindless drivel...

---

### Post by twittpro on 2011-07-11
Hello all, 

I am new to this forum, so sorry if this thread was solved or dead:o 

Also i am new Ubuntu User, so i installed the Ubuntu 11.04 on my PC and everything works perfectly except sound... 

I am going to youtube and playing a video, a video started playing but no sound, i have just installed ubuntu restriced extras bun not working.. so can you help me, i really need sound.. 

How can i take Alsa information and to post here with link.? 

Much appreciated

Regards

---

### Post by Illydth on 2011-07-17
I'm simply going to re-post what one of the last posters just did.

SOUND SEEMS TO GET SHIPPED ***MUTED*** IN 11.04.

Just installed mythbuntu 11.04 fresh on a new PC (re-architecting my previous MythTV architecture on new hardware).

Everything worked except sound.  First thing I noticed about Mythbuntu 11.04 was the fact that there is no tray icon for the sound mixer...it doesn't automatically start when you log into the interface.

I went into alsamixer from the command line but it didn't LOOK like anything was muted. *sigh*

Finally found the GUI mixer application in the menu system (you wouldn't think, with only like 30 menu items TOTAL in all of Mythbuntu that they could bury the mixer in a place it wouldn't be noticeable) and sure enough, both Master and PCM are muted by default (as seems to be pretty much everything else).

Right out of the box, fresh installation on pretty generic AC'97 hardware (NVidia NForce), and the sound is muted.

Really?  You guys at Ubuntu don't have ENOUGH e-mail and message board posts to reply to for help?  You need to turn off one of the 3 major subsystems in a working computer (Sound, Networking and Video) by default?

:)

RTFM Folks, in this case, the link at the top of the thread pointing at the Ubuntu Sound Trouble Shooting Document.

--Illydth

---

### Post by Maxchl on 2011-07-18
> **lidex said:**
> 
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

this + [ a mic uncheck via "System / prefrences / sound"]("https://wiki.ubuntu.com/Audio/CheckForMutedMicrophone")  after the reboot did the trick for me.

---

### Post by alan5700001 on 2011-07-26
I had the same problem. I upgraded to 11.04 and my sound wouldn't work at all. After searching for an eternity I found my solution.

I had to go into my sound preferences> Output tab> and then under the connector option change it from 'analog output/ amplifier' to 'analog output/ no amplifier' and my sound worked perfectly

---

### Post by waterandcoffee on 2011-07-27
Hi,

I tried several solutions you had listed here, but nothing seems to be working. I'm fairly new to linux so I hope this isn't a forehead slap of a fix.

Here is my alsa link: [http://www.alsa-project.org/db/?f=b20309980694fd4e3ef515de0683c3cdffa721e2](http://www.alsa-project.org/db/?f=b20309980694fd4e3ef515de0683c3cdffa721e2)

Thanks!

---

### Post by lovely-fake on 2011-07-31
Hi, I just installed Ubuntu 11.04 in my Asus K43U laptop. Having same sound problem. Its not unmute, already try and change the input/output but still no sound. Here's my Alsa Info [http://www.alsa-project.org/db/?f=c5ca4cf6c5120293a14ad0bab1dae59b5e1e40c5](http://www.alsa-project.org/db/?f=c5ca4cf6c5120293a14ad0bab1dae59b5e1e40c5) .. Can somebody help me to resolve this problem? Thanks in advance...

---

### Post by jgetz on 2011-07-31
Hi first time poster, long time reader. 

I've been searching for the better part of the last 3 weeks for a solution to my sound problem (i.e. no sound after update to Ubuntu 11.04) without success. It's disappointing that this upgrade has caused so much trouble...

If someone can help me identify what's wrong I would truly appreciate it plus it would allow me to get back to listening to my sweet tunes! 

My script can be found at [http://www.alsa-project.org/db/?f=901e5b1d37e77088e37a9d3c2e6a0f1db7b1c0f9](http://www.alsa-project.org/db/?f=901e5b1d37e77088e37a9d3c2e6a0f1db7b1c0f9).

Thanks!
-JGETZ

---

### Post by Asenov83 on 2011-08-02
Hi all! This is my first post here. I want to tell you my solution to this problem. First i was trying all from this tread, but no change. Still no sound. Finally i tried to plug the cable of my speakers to another exit(receptacle) of my sound card. I was using the green one with Windows XP, but now i put it in the blue and the sound started. I know that here are a lot of experienced users and maybe their problem is different from mine, but some may try this first before typing any codes and making any fundamental changes on the system. Sorry for my bad English. Good luck!

---

### Post by justinwhat on 2011-08-08
Holy crap, I've literally gone through this thread and exhaustively tried EVERY solution. Here's my info, any help would be appreciated.
[http://www.alsa-project.org/db/?f=0fd12f4f40fe74c58f0230a6758b0a36bf0c5cbe](http://www.alsa-project.org/db/?f=0fd12f4f40fe74c58f0230a6758b0a36bf0c5cbe)

---

### Post by lidex on 2011-08-16
> **waterandcoffee said:**
> Hi,

I tried several solutions you had listed here, but nothing seems to be working. I'm fairly new to linux so I hope this isn't a forehead slap of a fix.

Here is my alsa link: [http://www.alsa-project.org/db/?f=b20309980694fd4e3ef515de0683c3cdffa721e2](http://www.alsa-project.org/db/?f=b20309980694fd4e3ef515de0683c3cdffa721e2)

Thanks!

Is this a newer machine? Haven't seen that codec around. You left  the model=ref in alsa-base.conf and should remove it. I think the alc887 may actually be alc888. Can you post some Mobo info please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by bruno-b on 2011-08-18
Same problem here :( 

and here's the funny part:  once or twice when I booted my laptop the sound magically worked... so every time I boot I'm hoping for the magic to happen again.

it even gets weirder: sound from the jack plug works fine...  I can also put the plug into the mic socket (line in) and... yes, you guessed it..music plays on my headphone through the mic socket :confused:

I used to have both Vista and an older version of Ubuntu installed on the laptop and sound worked fine.. but now that I installed 11.04 it's giving me this problems 
 
On board mic seems to be working fine


Hopefully someone who understands this stuff is willingto have a look at my file:
[http://www.alsa-project.org/db/?f=0e8b7f6be450dd53eba12803a3de402503e1ae06](http://www.alsa-project.org/db/?f=0e8b7f6be450dd53eba12803a3de402503e1ae06)

thanks in advance :) cheers

Bruno

---

### Post by tru infini on 2011-08-19
This is the info that it gave me,... [http://www.alsa-project.org/db/?f=83781dec093458a638fe2c7205363b1a9679aa8c](http://www.alsa-project.org/db/?f=83781dec093458a638fe2c7205363b1a9679aa8c) any help?

The problem lies somewhere in my front headphone jack I have discovered. I typed in alsamixer into the terminal and it brought up my volume levels but the headphone volume level was grayed out and I couldn't do anything with it

---

### Post by lidex on 2011-08-22
> **tru infini said:**
> This is the info that it gave me,... [http://www.alsa-project.org/db/?f=83781dec093458a638fe2c7205363b1a9679aa8c](http://www.alsa-project.org/db/?f=83781dec093458a638fe2c7205363b1a9679aa8c) any help?

The problem lies somewhere in my front headphone jack I have discovered. I typed in alsamixer into the terminal and it brought up my volume levels but the headphone volume level was grayed out and I couldn't do anything with it


Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by akoswara on 2011-08-24
Hi all, 

I know that this thread should have been solved by now, but I thought I'd try to see if I can get a suggestion for solving the same problem I am having. 

I have read through the posts plus some others to see if I can switch on the volume, but to no avail. I have tried to update the module/driver for my intel HDA ALC269 VB, modify the sound options, and unmute via the alsamixer. Here is my alsa info, [http://www.alsa-project.org/db/?f=891d1b89df93151bf2789be7ba55e6cf58b52c5c](http://www.alsa-project.org/db/?f=891d1b89df93151bf2789be7ba55e6cf58b52c5c). Thanks much in advance!

---

### Post by cyberspeeyush on 2011-08-24
> **psilogon said:**
> **Try to determine the make of your sound card**

Run the following command in a terminal: 

```
aplay -l | grep card
``` This will probe your system, filtering lines that include the string 'card'. If you get results when you run this, you should be able to tell what make your sound card is. My results look like:

```
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
card 1: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
```If you have an Intel card, one thing that worked for me in the past is this: [http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html](http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html)



Thanks It worked for me...

---

### Post by lidex on 2011-08-24
> **akoswara said:**
> Hi all, 

I know that this thread should have been solved by now, but I thought I'd try to see if I can get a suggestion for solving the same problem I am having. 

I have read through the posts plus some others to see if I can switch on the volume, but to no avail. I have tried to update the module/driver for my intel HDA ALC269 VB, modify the sound options, and unmute via the alsamixer. Here is my alsa info, [http://www.alsa-project.org/db/?f=891d1b89df93151bf2789be7ba55e6cf58b52c5c](http://www.alsa-project.org/db/?f=891d1b89df93151bf2789be7ba55e6cf58b52c5c). Thanks much in advance!
Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```

```
ls /etc/modprobe.d/
```

---

### Post by akoswara on 2011-08-26
> **lidex said:**
> Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
``````
ls /etc/modprobe.d/
```

Here is the output:

cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=generic
options snd-hda-intel model=auto
options snd-hda-intel model=auto
options snd-hda-intel model=generic

ls /etc/modprobe.d/ 

alsa-base.conf                               blacklist-firewire.conf
alsa-base.conf.dpkg-old                      blacklist-framebuffer.conf
alsa-base options snd-hda-intel model=basic  blacklist-modem.conf
alsa-base options snd-hda-intel model=MODEL  blacklist-oss.conf
alsa-base.save                               blacklist-rare-network.conf
alsa-base.save.1                             blacklist-watchdog.conf
blacklist-ath_pci.conf                       libpisock9.conf
blacklist.conf

I really appreciate it!

---

### Post by lidex on 2011-08-27
Waaay too much going on there. Start by removing the unneeded files from modprobe.d:
```
sudo rm alsa-base.conf.dpkg-old alsa-base.save alsa-base.save.1
```
From alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove these lines:
```
options snd-hda-intel model=generic
options snd-hda-intel model=auto
options snd-hda-intel model=auto
options snd-hda-intel model=generic

```
Save. Close. Reboot.

---

### Post by ChetanKumar on 2011-08-27
No sound, tried everything in this forum, including adding lines to my alsa-conf-base, checking and re-checking my mute levels, checking the audio,pulse,pulse-acces in my user-groups... I

Here is my info... I'm sure the guy who fixes this will be a genius. Let's see which genius can work this out.

[http://www.alsa-project.org/db/?f=be681f664c83ff3d37499e6ec32c31c792ba8a5d](http://www.alsa-project.org/db/?f=be681f664c83ff3d37499e6ec32c31c792ba8a5d)

---

### Post by lidex on 2011-08-27
> **ChetanKumar said:**
> No sound, tried everything in this forum, including adding lines to my alsa-conf-base, checking and re-checking my mute levels, checking the audio,pulse,pulse-acces in my user-groups... I

Here is my info... I'm sure the guy who fixes this will be a genius. Let's see which genius can work this out.

[http://www.alsa-project.org/db/?f=be681f664c83ff3d37499e6ec32c31c792ba8a5d](http://www.alsa-project.org/db/?f=be681f664c83ff3d37499e6ec32c31c792ba8a5d)

Try these variations on your alsa-base.conf edit:
```
options snd-hda-intel model=auto position_fix=0
```
```
options snd-hda-intel model=alc260
```
```
options snd-hda-intel model=auto position_fix=-0
```

One at a time please. Reboot each time.

---

### Post by daten on 2011-08-27
I fixed this on an Alienware m17x laptop which has:

```
$ aplay -l | grep card
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
card 0: PCH [HDA Intel PCH], device 1: STAC92xx Digital [STAC92xx Digital]
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]

```

By running alsamixer and changing the "Mic Jack" column from "Line In" to "Mic In".

I don't know why this affects sound output, but nothing else mentioned in this thread worked until I changed that setting in alsamixer.

---

### Post by akoswara on 2011-08-28
> **lidex said:**
> Waaay too much going on there. Start by removing the unneeded files from modprobe.d:
```
sudo rm alsa-base.conf.dpkg-old alsa-base.save alsa-base.save.1
```
From alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove these lines:
```
options snd-hda-intel model=generic
options snd-hda-intel model=auto
options snd-hda-intel model=auto
options snd-hda-intel model=generic

```
Save. Close. Reboot.

Thank you for the suggestions. I have done them but the sound is still not available. Also, as it turns out, I did not have the following files to be removed: (1)alsa-base.conf.dpkg-old (2)alsa-base.savem, and (3) alsa-base.save.1.

---

### Post by lidex on 2011-08-28
> **akoswara said:**
> Thank you for the suggestions. I have done them but the sound is still not available. Also, as it turns out, I did not have the following files to be removed: (1)alsa-base.conf.dpkg-old (2)alsa-base.savem, and (3) alsa-base.save.1.

Let's see this again:
```
ls /etc/modprobe.d/
```
Post using code tags please.

---

### Post by akoswara on 2011-08-29
> **lidex said:**
> Let's see this again:
```
ls /etc/modprobe.d/
```
Post using code tags please.

Hi Lidex, 

Here is the results:

alsa-base.conf                               blacklist-firewire.conf
alsa-base.conf.dpkg-old                      blacklist-framebuffer.conf
alsa-base options snd-hda-intel model=basic  blacklist-modem.conf
alsa-base options snd-hda-intel model=MODEL  blacklist-oss.conf
alsa-base.save                               blacklist-rare-network.conf
alsa-base.save.1                             blacklist-watchdog.conf
blacklist-ath_pci.conf                       libpisock9.conf
blacklist.conf

So, I do have the files you suggested need to be removed. However, I don't have permission to do it. I am guessing that's the problem?

---

### Post by lidex on 2011-08-29
> **akoswara said:**
> Hi Lidex, 

Here is the results:

alsa-base.conf                               blacklist-firewire.conf
alsa-base.conf.dpkg-old                      blacklist-framebuffer.conf
alsa-base options snd-hda-intel model=basic  blacklist-modem.conf
alsa-base options snd-hda-intel model=MODEL  blacklist-oss.conf
alsa-base.save                               blacklist-rare-network.conf
alsa-base.save.1                             blacklist-watchdog.conf
blacklist-ath_pci.conf                       libpisock9.conf
blacklist.conf

So, I do have the files you suggested need to be removed. However, I don't have permission to do it. I am guessing that's the problem?

Sudo gives you the permission - did you use the command as written? Anyway all this needs to go:
```
alsa-base.conf.dpkg-old                      
[COLOR="Red"]alsa-base options snd-hda-intel model=basic  
alsa-base options snd-hda-intel model=MODEL [/COLOR]
alsa-base.save                               
alsa-base.save.1                 
```

I'm not sure how you got the two lines in red in there. It may be easier for you to use nautilus as root. 
Be careful as you can remove critical system files and render your install unusable.
```
gksu nautilus
```

---

### Post by akoswara on 2011-08-30
> **lidex said:**
> Sudo gives you the permission - did you use the command as written? Anyway all this needs to go:
```
alsa-base.conf.dpkg-old                      
[COLOR="Red"]alsa-base options snd-hda-intel model=basic  
alsa-base options snd-hda-intel model=MODEL [/COLOR]
alsa-base.save                               
alsa-base.save.1                 
```

I'm not sure how you got the two lines in red in there. It may be easier for you to use nautilus as root. 
Be careful as you can remove critical system files and render your install unusable.
```
gksu nautilus
```

Hi Lidex, Thanks much!! I use nautilus as root as you suggested and was able to delete the files and restore the sound. On a side note, I did use the sudo rm code as it is to try to remove the files the first time and then again this time, but it still says no such file in the directory exists (eventhough it's clearly there). I would leave this issue for another time to solve. Thank you again. I really do appreciate it.

---

### Post by lidex on 2011-08-30
> **akoswara said:**
> Hi Lidex, Thanks much!! I use nautilus as root as you suggested and was able to delete the files and restore the sound. On a side note, I did use the sudo rm code as it is to try to remove the files the first time and then again this time, but it still says no such file in the directory exists (eventhough it's clearly there). I would leave this issue for another time to solve. Thank you again. I really do appreciate it.

You're welcome. In the future if your mucking about in that directory remove anything you added that doesn't work and store any backups in your home directory.

---

### Post by mfractal on 2011-09-01
@lidex, could you please take a look at my result ?
[http://www.alsa-project.org/db/?f=1c8bb25199f63df42a3b409a824feda2cdbf16ab](http://www.alsa-project.org/db/?f=1c8bb25199f63df42a3b409a824feda2cdbf16ab)

i went over this thread and tried your suggestions but i still get no sound.

Would greatly appreciate your help!

---

### Post by lidex on 2011-09-02
> **mfractal said:**
> @lidex, could you please take a look at my result ?
[http://www.alsa-project.org/db/?f=1c8bb25199f63df42a3b409a824feda2cdbf16ab](http://www.alsa-project.org/db/?f=1c8bb25199f63df42a3b409a824feda2cdbf16ab)

i went over this thread and tried your suggestions but i still get no sound.

Would greatly appreciate your help!

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=alienware" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by mfractal on 2011-09-02
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=alienware" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**


Unfortunately that didn't work.
i also tried this suggestion from the previous page to no avail :


> **daten said:**
> I fixed this on an Alienware m17x laptop which has:

```
$ aplay -l | grep card
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
card 0: PCH [HDA Intel PCH], device 1: STAC92xx Digital [STAC92xx Digital]
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]

```By running alsamixer and changing the "Mic Jack" column from "Line In" to "Mic In".

I don't know why this affects sound output, but nothing else mentioned  in this thread worked until I changed that setting in alsamixer.


Anything else i could try ?


EDIT :
messed it up some more..
i saw your post [here]("http://ubuntuforums.org/showpost.php?p=9623296&postcount=12") and followed that procedure. Now even the sound volume icon doesn't appear....

here's the updated situation:
[http://www.alsa-project.org/db/?f=38fca3d3f2189c2f6b7191da5973331331575f67](http://www.alsa-project.org/db/?f=38fca3d3f2189c2f6b7191da5973331331575f67)

---

### Post by lidex on 2011-09-02
> **mfractal said:**
> Unfortunately that didn't work.
i also tried this suggestion from the previous page to no avail :





Anything else i could try ?


EDIT :
messed it up some more..
i saw your post [here]("http://ubuntuforums.org/showpost.php?p=9623296&postcount=12") and followed that procedure. Now even the sound volume icon doesn't appear....

here's the updated situation:
[http://www.alsa-project.org/db/?f=38fca3d3f2189c2f6b7191da5973331331575f67](http://www.alsa-project.org/db/?f=38fca3d3f2189c2f6b7191da5973331331575f67)

Do not despair, my friend. I'll need you to clean up alsa-base.conf and remember anytime you edit a config files' default values and it doesn't work, remove those changes (revert to default) before trying anything else. To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove anything beginning with:
```
options snd-hda-intel
```
Next add this line at the bottom:
```
options snd-hda-intel model=alienware
```
Save. Close. Reboot. Check alsamixer and sound preferences.

---

### Post by kieran739 on 2011-09-03
I have no sound at all. 

this is what i get 

[http://www.alsa-project.org/db/?f=2681318b06b87efc15cc6ae4342367b766cea0bb](http://www.alsa-project.org/db/?f=2681318b06b87efc15cc6ae4342367b766cea0bb)

Would it just be easier to buy a new sound card ? would that solve it ?

---

### Post by mfractal on 2011-09-03
> **lidex said:**
> Do not despair, my friend. I'll need you to clean up alsa-base.conf and remember anytime you edit a config files' default values and it doesn't work, remove those changes (revert to default) before trying anything else. To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```Remove anything beginning with:
```
options snd-hda-intel
```Next add this line at the bottom:
```
options snd-hda-intel model=alienware
```Save. Close. Reboot. Check alsamixer and sound preferences.

thanks for the support, i appreciate it.
I've done exactly what you asked me to and there is currently no sound and no volume icon present.

hope you got more ideas up your sleeve :)

do you need me to post any information ?

---

### Post by lidex on 2011-09-04
> **kieran739 said:**
> I have no sound at all. 

this is what i get 

[http://www.alsa-project.org/db/?f=2681318b06b87efc15cc6ae4342367b766cea0bb](http://www.alsa-project.org/db/?f=2681318b06b87efc15cc6ae4342367b766cea0bb)

Would it just be easier to buy a new sound card ? would that solve it ?
Looks like you tried to upgrade alsa unsuccessfully. Follow the link in my sig for the alsa-upgrade script and retry that process.

---

### Post by lidex on 2011-09-04
> **mfractal said:**
> thanks for the support, i appreciate it.
I've done exactly what you asked me to and there is currently no sound and no volume icon present.

hope you got more ideas up your sleeve :)

do you need me to post any information ?

Show your amixer output:
```
amixer
```

---

### Post by mfractal on 2011-09-04
> **lidex said:**
> Show your amixer output:
```
amixer
```

thanks for not giving up on me :)
```

mfractal@avenger:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [-1.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2' 'Off'
  Item0: 'Digital Playback'
Simple mixer control 'IEC958 Playback Source',1
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2' 'Off'
  Item0: 'Digital Playback'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

```

---

### Post by Checkrune on 2011-09-05
Hey everybody!  I was having issues with my sound in 11.04, and by following Lidex's instructions after a Google Search, I was able to fix my sound issue.  So I suscribed to this forum in order thank you for the time you take to help others!  That's really great from you!

---

### Post by omlx2 on 2011-09-06
hi ,,,
i tried to find a solution since 3days,,but no use 
i reinstalled Ubuntu 11.04 yesterday but still sound is not working
   
  [http://www.alsa-project.org/db/?f=f2bcd09443159a06554e437a6a95716c15643066](http://www.alsa-project.org/db/?f=f2bcd09443159a06554e437a6a95716c15643066)

am looking forward for your support

---

### Post by Khan_77 on 2011-09-10
no sound on my ASUS eee pc too
following is the link to alsa script result
[http://www.alsa-project.org/db/?f=a4f519a1797866e2479463e5a18dbdebce84581b](http://www.alsa-project.org/db/?f=a4f519a1797866e2479463e5a18dbdebce84581b)

---

### Post by Denver Dave on 2011-09-14
Same issue here (I think).  I'm running from the 11.04 DVD and did manage to get Adobe Flash turned on.  However, when I watch Youtube videos there is no sound.  I'm not sure if there is sound for other things - not sure how to test.

I'm wondering if there is a preferred solution?  They all seem pretty techie.

At least one "solution" involved rebooting which means the change would not remain since I'm running the DVD.  

I'm on a Compaq formerly XP PC.

Not clear what the issue is and what the various "solutions" are attempting to accomplish.

---

### Post by N1ck0s on 2011-09-17
Hello everyone! I have the same problem, and i have tried everything above (well, i am not sure if i have done any mistakes) but my pc does not play sound. But that is weird, because when the installation was fresh, sound worked just fine and it suddenly stopped (not after update or something) after a shutdown. Plz help!

[http://www.alsa-project.org/db/?f=e746a1f7c78719593910ccec24d76cf3e0d174a3](http://www.alsa-project.org/db/?f=e746a1f7c78719593910ccec24d76cf3e0d174a3)

---

### Post by lidex on 2011-09-17
> **mfractal said:**
> thanks for not giving up on me :)
```

mfractal@avenger:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [-1.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2' 'Off'
  Item0: 'Digital Playback'
Simple mixer control 'IEC958 Playback Source',1
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2' 'Off'
  Item0: 'Digital Playback'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

```

Sorry bro. Was out of town. Amixer looks OK. Post an updated alsa-info please.

---

### Post by lidex on 2011-09-18
> **omlx2 said:**
> hi ,,,
i tried to find a solution since 3days,,but no use 
i reinstalled Ubuntu 11.04 yesterday but still sound is not working
   
  [http://www.alsa-project.org/db/?f=f2bcd09443159a06554e437a6a95716c15643066](http://www.alsa-project.org/db/?f=f2bcd09443159a06554e437a6a95716c15643066)

am looking forward for your support

Whenever you add something to a configuration file and it doesn't work, remove it before trying something else. I'll need you to edit alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove any lines beginning with "options snd-hda-intel". Save. Close. Reboot. Now post an updated alsa-info.

---

### Post by lidex on 2011-09-18
> **Khan_77 said:**
> no sound on my ASUS eee pc too
following is the link to alsa script result
[http://www.alsa-project.org/db/?f=a4f519a1797866e2479463e5a18dbdebce84581b](http://www.alsa-project.org/db/?f=a4f519a1797866e2479463e5a18dbdebce84581b)

I was subscribed to a bug report on your codec. Thinking the fix is in the pipeline. Follow the link in my sig to upgrade alsa to latest version.

---

### Post by lidex on 2011-09-18
> **N1ck0s said:**
> Hello everyone! I have the same problem, and i have tried everything above (well, i am not sure if i have done any mistakes) but my pc does not play sound. But that is weird, because when the installation was fresh, sound worked just fine and it suddenly stopped (not after update or something) after a shutdown. Plz help!

[http://www.alsa-project.org/db/?f=e746a1f7c78719593910ccec24d76cf3e0d174a3](http://www.alsa-project.org/db/?f=e746a1f7c78719593910ccec24d76cf3e0d174a3)

Go into alsamixer and unmute your channels.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by N1ck0s on 2011-09-18
> **lidex said:**
> Go into alsamixer and unmute your channels.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
  Problem solved! Thanks a lot! Even the microphone works! I am going to listen to music all day!!! :p:p:p

---

### Post by raj_tgin on 2011-10-05
I have installed Ubuntu 11.04..but no sound is coming from Creative sound blaster live card but sound is played thru onboard sound card.

The 2 cards shown in mixer are
CA0106
ESS Allegro PCI

I tried many work arounds from may sites but nothing worked and I could get my CA0106 play the sound.

I was using Mint 11 previous which had detected no issues..Could anyone help me

---

### Post by raj_tgin on 2011-10-05
> **raj_tgin said:**
> I have installed Ubuntu 11.04..but no sound is coming from Creative sound blaster live card but sound is played thru onboard sound card.

The 2 cards shown in mixer are
CA0106
ESS Allegro PCI

I tried many work arounds from may sites but nothing worked and I could get my CA0106 play the sound.

I was using Mint 11 previous which had detected no issues..Could anyone help me



Here is the details of sound card

[http://www.alsa-project.org/db/?f=00964bb59539d68256f202dbc9f4866bdb9f54de](http://www.alsa-project.org/db/?f=00964bb59539d68256f202dbc9f4866bdb9f54de)

---

### Post by mfractal on 2011-10-05
> **lidex said:**
> Sorry bro. Was out of town. Amixer looks OK. Post an updated alsa-info please.

Missed your message... Here it is : [http://www.alsa-project.org/db/?f=a199074242cf34d3e022f2d8dfb47eb69b41aa55](http://www.alsa-project.org/db/?f=a199074242cf34d3e022f2d8dfb47eb69b41aa55)


I also saw that a user reported that same problem with my model (alienware m18x) and he successfully got sound to work :

> added the line "options snd-hda-intel model=dell-m6-amic" at the end of 
/etc/modprobe.d/alsa-base.conf


[http://old.nabble.com/-Bug-273763--New%3A-kubuntu-11.04-on-Alienware-m18x---get-no-sounds-at-all-except-through-headset.-No-pulseaudio-backend-td31668118.html](http://old.nabble.com/-Bug-273763--New%3A-kubuntu-11.04-on-Alienware-m18x---get-no-sounds-at-all-except-through-headset.-No-pulseaudio-backend-td31668118.html)


his solution didn't work for me though...

---

### Post by lidex on 2011-10-11
> **raj_tgin said:**
> Here is the details of sound card

[http://www.alsa-project.org/db/?f=00964bb59539d68256f202dbc9f4866bdb9f54de](http://www.alsa-project.org/db/?f=00964bb59539d68256f202dbc9f4866bdb9f54de)
Have you tried disabling onboard audio in the bios?

---

### Post by lidex on 2011-10-11
> **mfractal said:**
> Missed your message... Here it is : [http://www.alsa-project.org/db/?f=a199074242cf34d3e022f2d8dfb47eb69b41aa55](http://www.alsa-project.org/db/?f=a199074242cf34d3e022f2d8dfb47eb69b41aa55)


I also saw that a user reported that same problem with my model (alienware m18x) and he successfully got sound to work :

[http://old.nabble.com/-Bug-273763--New%3A-kubuntu-11.04-on-Alienware-m18x---get-no-sounds-at-all-except-through-headset.-No-pulseaudio-backend-td31668118.html](http://old.nabble.com/-Bug-273763--New%3A-kubuntu-11.04-on-Alienware-m18x---get-no-sounds-at-all-except-through-headset.-No-pulseaudio-backend-td31668118.html)


his solution didn't work for me though...

Try removing all the other cruft from alsa-base.conf:
```
snd-hda-intel: model=dell-m6-amic
snd-hda-intel: enable_msi=1
snd-hda-intel: single_cmd=1
snd-hda-intel: model=dell-m6-amic position_fix=1 enable=yes

```
Leave only the first line

---

### Post by mfractal on 2011-10-11
> **lidex said:**
> Try removing all the other cruft from alsa-base.conf:
```
snd-hda-intel: model=dell-m6-amic
snd-hda-intel: enable_msi=1
snd-hda-intel: single_cmd=1
snd-hda-intel: model=dell-m6-amic position_fix=1 enable=yes

```
Leave only the first line

Still no sound from the speakers...
here's the config now :
[http://www.alsa-project.org/db/?f=3e134ceeffca0f5907fe29bcae775d09b178ee56](http://www.alsa-project.org/db/?f=3e134ceeffca0f5907fe29bcae775d09b178ee56)

i am losing hope here .. :(

---

### Post by hellsfire2 on 2012-02-07
Good evening , first post iin this interesting forum and  new in ubuntu-linux. Installation of ubuntu 11.04 went fine but i have no sound at all.
[http://www.alsa-project.org/db/?f=7fe148205f5a689787c235601782da4f547ff136](http://www.alsa-project.org/db/?f=7fe148205f5a689787c235601782da4f547ff136)
Thank you in advance for your advice

---

