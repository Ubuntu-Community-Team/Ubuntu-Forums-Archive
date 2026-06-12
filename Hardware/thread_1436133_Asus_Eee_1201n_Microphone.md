---
title: "Asus Eee 1201n Microphone"
date: 2010-03-22
forum: Hardware
---

### Post by hsoulen on 2010-03-22
HI folks,

Hope there is some advice out there.

I have an Asus Eee 1201n which is running Karmic very well, had a couple of issues with wireless but thanks to Realtek support for Linux they released a driver that works perfectly with more recent kernels (2.6.31-20). Quick side note, if you are running this netbook do yourself a favor and try "rtl8192se_linux_2.6.0015.0127.2010"  before you use NDISWrapper etc. 

OK, back on topic. Last thing I have left is the built-in microphone (NVIDIA ION HD Audio). GNOME Alsa Mixer sees it, so does the GNOME sound panel, Skype sees it as well but no go. I have tried Alsa backports to no result. There is a thread in these forums for a script (Alsa upgrade script) and although I thank the dude who wrote it I am paranoid as he explicitly says:

"The script is not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files. You won't see any changes on the ALSA package-ids within Synaptic!" 

And this scares me just a bit. I am about to try this script as I am just plain tired of Skype with a BT headset (my wife calls me a cyborg) so before I kick it off I thought I would ping the "Gurus" and see if there are any other suggestions out there.

Thanks in advance!

Hank.

Solved... Installed the pulseaudio utility and set the 2nd mic channel to 0.

---

### Post by scstubbs on 2010-04-16
Hello,

I have the same computer and the same problem. Could you please give me the steps you took to installing pulseaudio util and using it. I am a noob but am learning a lot. Sadly I just can't figure out how to set those settings to zero like you said.

Thank you for your help and time!

---

### Post by hsoulen on 2010-04-16
> **scstubbs said:**
> Hello,

I have the same computer and the same problem. Could you please give me the steps you took to installing pulseaudio util and using it. I am a noob but am learning a lot. Sadly I just can't figure out how to set those settings to zero like you said.

Thank you for your help and time!

Sure man, hope this helps:

I am not sure of your level of Linux experience so don't take any offense if these instructions are too verbose.

1) Open Synaptic Package Mananger from System->Administration
2) Search for a package with a name like "linux-backports-modules-alsa-karmic-generic" (it will have the name of your distribution, karmic if you have 9.10, lucid if you are running the 10.04 LTS Beta etc.) and mark it for install
3) Still in Synaptic, search for a package called "pavucontrol" (PulseAudio Volume Control) and mark it for install as well
4) Hit "Apply" and after the packages have downloaded and installed, reboot linux
5) Once you log back in, go to Applications->Sound & Video and run "PulseAudio Volume Control"
6) Click the "Input Devices" tab and you will see your mic but it will have two channels (stereo) a Front Right and Front Left. Well this is just plain wrong! A mic is a mono device, so go ahead and set that Front Right slider all the way to "Silence" (you can leave Front Left at about 80-90%)

Exit PulseAudio Volume Control and you should now have a working mic in all applications including Skype if you use it.

Cheers,

Hank

---

### Post by welshmike on 2010-04-18
Thanks Hank,

I have an ASUS Eec PC 1001P.

Following your advice got my sound recorder to record sound. However Skype still does not record.

Mike

---

### Post by hsoulen on 2010-04-20
> **welshmike said:**
> Thanks Hank,

I have an ASUS Eec PC 1001P.

Following your advice got my sound recorder to record sound. However Skype still does not record.

Mike

Hi Mike,

Glad we got something working :)

Quick question, under Skype->Options->Sound Devices, what does it show? It should show "PulseAudio Server (local)" for all options, also I found that "Allow Skype to automatically adjust my mixer levels" does NOT WORK! In order for my mic to work in Skype I have to un-check that option.

Also what version of Skype are you using? I am on Beta 2.1.0.81.

Let me know if this helps, if not we can take a deeper look.

Hank

---

### Post by welshmike on 2010-04-20
> **hsoulen said:**
> Hi Mike,

Glad we got something working :)

Quick question, under Skype->Options->Sound Devices, what does it show? It should show "PulseAudio Server (local)" for all options, also I found that "Allow Skype to automatically adjust my mixer levels" does NOT WORK! In order for my mic to work in Skype I have to un-check that option.

Also what version of Skype are you using? I am on Beta 2.1.0.81.

Let me know if this helps, if not we can take a deeper look.

Hank

Hi Hank,

Apologies from the following long post but it may help other forum members.

I'm also on Skype Beta 2.1.0.81.

I believe that it is not a Skype problem but a PulseAudio one.

Skype did show "PulseAudio Server (local)" for all options. There were no other options.
I unchecked "Allow Skype to automatically adjust my mixer levels".
No recording made from inbuilt microphone (using Echo / Sound Test Service"

Ubuntu System > Preferences > Sound > Input shows no Input level bar movement when I speak into builtin microphone.
However when I plugged in an external microphone the bars moved.
Great - It worked and so did Skype sound recording.
So I looked at Ubuntu System > Preferences > Sound > Input > Choose a device for sound input and it showed "Internal Audio Analog Stereo"
That looks correct for the builtin mike. So I ask myself why does external one worK???
Hardware showed Internal Audio 1 Output/1 Input Analog Stereo Duplex.
When I click Sound Effects > Choose an alert sound: I get the appropriate sound I click like Default or Bark, etc.

When I boot ASUS Express Gate (which I believe is a tiny Linux based distro) and select Skype I found that the Sound devices that worked are
Sound In: HDA Intel (hw:Intel.0)
Sound Out: HDA Intel (hw:Intel.0)

Maybe I have a sound driver problem?.

So being a retired R&D system software engineer I had a play around:
Using Ubuntu Software center 
- I removed all PulseAudio stuff - problem unsolved.
- Installed Default Sound Card (ALSA) - problem unsolved
- Installed GNOME ALSA Mixer. I noticed Mic Boos was at bottom of slider and balance (left right) could not be moved. Capture Rec was ticked - problem unsolved. I unticked Rec - problem unsolved. I reticked Rec - PROBLEM SOLVED. SKYPE RECORDING WORKS ON INTERNAL MIKE!!!
Just to be sure I rebooted Ubuntu.
Skype recording still works on internal Mike.
Tried my external boom mike  It works but lots of buzzing even at no or less than amplified input. It is fine on my old laptop but needs input amplified.

Regards
Mike

---

### Post by hsoulen on 2010-04-21
Thanks for posting this back Mike, that's great news!

My fault entirely for not adding that I have ALSA Mixer installed as  well, I did not have to check/un-check the Capture Rec tickbox to get mine working, but then again I had ALSA mixer installed early in my attempts to rectify the problem so perhaps I had done that a few times before getting the ALSA backports installed.

Always nice when folks post back their solutions.

There is just far to much confusion in the Linux World right now in Sound and Video APIs in general, so much so that we can't even get proper Hardware Acceleration in Flash for Linux because they can't pick a proper API.

Nice paper on the sound API issue at this link: [http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)

From 2008 but still applies today...

Think I am going to spend a bit of time removing the rust from my C/C++ and get a bit more involved, just hope I can do more good than harm :P

Hank

---

### Post by welshmike on 2010-04-21
Hank

You are a jolly good egg.

It is really sad that the vast majority of home Personal Computer users use Microsoft operating systems.
Such systems have all the security flaws and performance degradation inherent in the design of Windows since XP and maybe before.
The concept and implementation of the Windows Registry and of the DLL hell is in my opinion the Achilles Heel of Redmond's outpourings.
I've spent a lot of my retirement bailing out friends and neighbours from broken Microsoft systems.

[I]The latest victim (a lady friend of a friend) of Microsoft opsys vulnerabilities (XP) had 170 infected files, seven or more different types of viruses including a rogue dialler, keytroke recorder, trojan horse, email worm and two rootkit viruses.
With the help of online forums and use of Malwarebytes, etc., I was able to clean up her sick XP system but the rootkit viruses remained.
I was able to save all her irreplaceable data onto an external USB HDD by booting from an Ubuntu live CD.
Her desktop PC had an XP recovery partition so I was able to reset the PC to factory condition and then installed her vital applications and restored her data. I had earned the big hug she gave me :) [/I]

One has to recognise Microsoft's formidable success as a result of their aggressive marketing. A pity that IBM did not target and market OS/2 to home users as well as Companies.

I too, as a retired R&D software engineer, would like to contribute to Ubuntu's success. I guess that IBM Assembler does not have much call today but I can hack it a bit in PHP.

All the best
Mike

---

### Post by mercnet on 2010-05-01
> **hsoulen said:**
> Sure man, hope this helps:

I am not sure of your level of Linux experience so don't take any offense if these instructions are too verbose.

1) Open Synaptic Package Mananger from System->Administration
2) Search for a package with a name like "linux-backports-modules-alsa-karmic-generic" (it will have the name of your distribution, karmic if you have 9.10, lucid if you are running the 10.04 LTS Beta etc.) and mark it for install
3) Still in Synaptic, search for a package called "pavucontrol" (PulseAudio Volume Control) and mark it for install as well
4) Hit "Apply" and after the packages have downloaded and installed, reboot linux
5) Once you log back in, go to Applications->Sound & Video and run "PulseAudio Volume Control"
6) Click the "Input Devices" tab and you will see your mic but it will have two channels (stereo) a Front Right and Front Left. Well this is just plain wrong! A mic is a mono device, so go ahead and set that Front Right slider all the way to "Silence" (you can leave Front Left at about 80-90%)

Exit PulseAudio Volume Control and you should now have a working mic in all applications including Skype if you use it.

Cheers,

Hank

This worked perfectly for me with my 1201N running 10.04 thanks!

---

### Post by temporos on 2010-05-08
Unfortunately, neither of these solutions worked for me.  I can record sounds in the "Sound Recorder" application, but not in Skype.  I tried using the PulseAudio and GNOME ALSA Mixer, but neither worked.  Any other suggestions?

---

### Post by lidex on 2010-05-08
> **temporos said:**
> Unfortunately, neither of these solutions worked for me.  I can record sounds in the "Sound Recorder" application, but not in Skype.  I tried using the PulseAudio and GNOME ALSA Mixer, but neither worked.  Any other suggestions?

Try this. Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Reboot.

---

### Post by proze on 2010-05-13
The original solution worked for me as well, but I had to have GNOME Alsa Mixer installed as well. Random, but at least it's working now. Sheesh.

---

### Post by temporos on 2010-05-13
Yeah, I still can't get it to work.  Since the only application for which the mic won't work is Skype, I'm just going to dump Skype and try Google Talk on Empathy instead...  It can do video chat, right?

---

### Post by lidex on 2010-05-13
What version of skype are you using?

---

### Post by temporos on 2010-05-14
> **lidex said:**
> What version of skype are you using?
Skype v2.1b2.  It was the only version available on their [web site](http://www.skype.com) when I downloaded it a few weeks ago.

---

### Post by nrayever on 2010-09-04
> **hsoulen said:**
> Sure man, hope this helps:

I am not sure of your level of Linux experience so don't take any offense if these instructions are too verbose.

1) Open Synaptic Package Mananger from System->Administration
2) Search for a package with a name like "linux-backports-modules-alsa-karmic-generic" (it will have the name of your distribution, karmic if you have 9.10, lucid if you are running the 10.04 LTS Beta etc.) and mark it for install
3) Still in Synaptic, search for a package called "pavucontrol" (PulseAudio Volume Control) and mark it for install as well
4) Hit "Apply" and after the packages have downloaded and installed, reboot linux
5) Once you log back in, go to Applications->Sound & Video and run "PulseAudio Volume Control"
6) Click the "Input Devices" tab and you will see your mic but it will have two channels (stereo) a Front Right and Front Left. Well this is just plain wrong! A mic is a mono device, so go ahead and set that Front Right slider all the way to "Silence" (you can leave Front Left at about 80-90%)

Exit PulseAudio Volume Control and you should now have a working mic in all applications including Skype if you use it.

Cheers,

Hank

Thanks man! it worked like a charm! great howto.

---

### Post by Cylon on 2011-03-14
This does work for me on my EEE PC 1201n. However, about 15 seconds into any conversation the left channel goes back to 100% entirely on its own. It also resets itself to be locked with the right channel. I've tested this in both Ubuntu 10.10 and Linux Mint with the same results.

Interestingly, if I use a Bluetooth headset I end up having the same issues about 15 seconds into any conversation whether it be on Skype or Google Talk.

---

### Post by lidex on 2011-03-18
> **Cylon said:**
> This does work for me on my EEE PC 1201n. However, about 15 seconds into any conversation the left channel goes back to 100% entirely on its own. It also resets itself to be locked with the right channel. I've tested this in both Ubuntu 10.10 and Linux Mint with the same results.

Interestingly, if I use a Bluetooth headset I end up having the same issues about 15 seconds into any conversation whether it be on Skype or Google Talk.

Have you disabled the skype setting to allow it to control levels?

---

### Post by doraemonppc on 2011-05-26
Hello.
I've tryed all the sollutions without success.
I can record soud but the mic dont work on skype or gtalk
I'm running in a 11.04 ubuntu.
Anyone can help-me?
Sorry for my bad english

---

### Post by liam.carroll on 2011-08-22
I had the same microphone issue in skype on ubuntu 11.04. however, i could not apply the fix because no left/right channels were shown for the microphone. they do exist. until i chose to 'show all except monitors', however, i could not see them. THIS FIX WORKS IN UBUNTU 11.04 TOO but it seems pulseaudio volume control interface has been reworked from previous major release. hope this helps

---

### Post by waldherrvonbirnbaum on 2011-12-28
oh man, you made my day! last solution worx perfect on eee 1001ha with the newest skype and 10.4 ubuntu. thx!

---

