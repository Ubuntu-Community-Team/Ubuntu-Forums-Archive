---
title: "No sound after resuming from suspend/hibernate"
date: 2008-11-08
forum: General Help
---

### Post by Jephir on 2008-11-08
I'm having trouble with suspend/hibernate on my computer. After resuming from suspend/hibernate, there's no sound at all in Ubuntu. The volume control is not muted, but no sounds play from Ubuntu or any application. The only fix I know is to restart Ubuntu.

When I ran Windows on this computer, there was no problems with sound after resuming from suspend/hibernate.

My motherboard is an Asus P5K SE, and my sound card is an Asus Xonar DX.

Any help would be greatly appreciated.

---

### Post by gingerlizard on 2008-11-10
I recently upgraded from Hardy Heron to Intrepid Ibex on my IBM Thinkpad T23 - and initially had a reoccurance of an old HH problem of no sound after resuming from hibernate.

On HH I sorted it with the recommended [fix]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T23#Sound_After_Suspend").

However the fix seemed to be ineffective with Intrepid Ibex.

But tried removing the fix - and reapplying it - sorted.

---

### Post by kpothi on 2008-11-12
Hi all,

I too have the same issue. Kindly post your solution, if you have.

I tried the fix mentioned in the previous post. It didn't work for me.

I too have the Asus motheboard. I don't know how to find the sound card manufacturer information. I do not have any other OS installed in this desktop PC. Ubuntu 8.04 is the only operating system. Please help. Currently, the only way I could get the sound is by rebooting the PC.

Thanks a lot in advance.

---

### Post by philinux on 2008-11-12
Intrepid fixed this bugette for me. In Hardy I had to do this from the terminal.

```
sudo alsa force-reload
```

Better than rebooting.

---

### Post by mlissner on 2008-11-12
Sigh. Intrepid CAUSED this bug for me.

---

### Post by GnuSense on 2008-11-22
I had this problem with Hardy after a hibernate.  restarting alsa-utils & pulseaudio didn't help (e.g. *sudo /etc/init.d/pulseaudio restart*), and I still had no sound after rebooting!    

philinux's force-reload command worked for me, thanks, I'll try to remember that one.  I wonder why Ubuntu abandoned Debian's alsaconf.

I'd just had a problem with Hardy sound maybe a week ago when after a kernel upgrade sound & compiz fusion didn't work (white screen).  I found that booting 2.6.24-21-generic instead of 2.6.24-21-386 worked for me.  I get the feeling that the 24.21 kernels are causing a fair number of problems.  C'mon guys, Hardy is a LTS version, I'm NOT upgrading to Intrepid because I want that extra stability (and I HATE KDE 4; I switch off between Gnome and KDE 3.5).

---

### Post by christoforever on 2008-11-26
Yea I have the same problem. No sound after hibernate, though i must say my hibernate is actually working compared to previous releases and wakes up awfully fast, which is a great thing. But not sound. The fix that phillix gave works however.

---

### Post by pigSTI04 on 2008-12-03
> **gingerlizard said:**
> I recently upgraded from Hardy Heron to Intrepid Ibex on my IBM Thinkpad T23 - and initially had a reoccurance of an old HH problem of no sound after resuming from hibernate.

On HH I sorted it with the recommended [fix]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T23#Sound_After_Suspend").

However the fix seemed to be ineffective with Intrepid Ibex.

But tried removing the fix - and reapplying it - sorted.

What do you know, I just did the same thing the other day on my t23 and I now have no sound after suspend mode. I'm going to give your fix a try.

Anyone else had success?

---

### Post by brianpeiris on 2009-02-15
> **philinux said:**
> Intrepid fixed this bugette for me. In Hardy I had to do this from the terminal.

```
sudo alsa force-reload
```

Better than rebooting.

Thanks phillinux, that fixed my sound after suspend on intrepid.

---

### Post by Jephir on 2009-04-29
> **philinux said:**
> Intrepid fixed this bugette for me. In Hardy I had to do this from the terminal.

```
sudo alsa force-reload
```

Better than rebooting.

Yep, this makes sound work again after suspending in Ubuntu 9.04.

Is there any way to automatically run this command after resuming from suspend?

---

### Post by Antioch on 2009-05-11
I'd like to know this as well.

Also, in my case after resume the USB keyboard doesn't work. I have to plug it into a different slot before I can use it again... and ideas?

---

### Post by Antioch on 2009-05-11
[https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate)

There are directions for getting alsa to automatically restart after resume.

Enjoy!

---

### Post by frogotronic on 2009-07-10
> **Antioch said:**
> I'd like to know this as well.

Also, in my case after resume the USB keyboard doesn't work. I have to plug it into a different slot before I can use it again... and ideas?

check out my blog its got a solution [http://toothfish.blogspot.com/2009/02/docking-station-usb-workaround.html](http://toothfish.blogspot.com/2009/02/docking-station-usb-workaround.html)

try "lsusb"

---

### Post by frogotronic on 2009-07-10
> **pigSTI04 said:**
> What do you know, I just did the same thing the other day on my t23 and I now have no sound after suspend mode. I'm going to give your fix a try.

Anyone else had success?

Just tried this and it works - awesome!

---

### Post by jhunt31 on 2009-07-17
Heyas,

I came across this thread through Google as a new user of Ubuntu searching for a fix to the same issue. I have similar hardware to the OP, Jephir:
Motherboard: Asus P5K
Soundcard: Xonar DX
with an E6420, 8800GTS

As above, the [link]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate") provided by Antioch enables you to reload ALSA after suspending your computer. I was having problems getting it to work, as you additionally need to enable 'Allow executing file as a program".

Here's the full instructions with the added last step:
> 
Open a terminal then run the command below
```
sudo nano /etc/pm/sleep.d/50alsa
```(Or gedit/whatever other text editor)

Copy and paste the below code then save and close the file
```
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload
                ;;
        *) exit $NA
                ;;
esac
```Now run in the terminal
```
sudo nautilus /etc/pm/sleep.d
```Right-click on the 50alsa file and select Properties

Go to the Permissions tab

Tick the box next to Execute - "Allow executing file as a program"And that's it!  When you come out of suspend there'll be a pop up for "Volume Control" has quit unexpectedly. Just click on Reload. Also any programs that use ALSA (I guess? I'm not exactly sure, but Skype isn't affected) will crash - eg. Banshee won't work and will die shortly after I press play. Just restart those programs and everything should be sweet! 

Good luck, I hope it works for you. :D

---

### Post by jukingeo on 2009-09-13
Hello all,

I have the same problem as listed above:  No sound after hibernate/suspend.  However, in my case NONE of the above solutions has worked.  In order to get my sound back I have ALWAYS had to reboot my machine.

I am running Alsa on a Dell Dimension 4600 with Ubuntu Hardy (8.04).  I have an M-Audio Delta 44 sound card I am using with Envy 24 control.

I find it kind of stupid that Ubuntu shuts off the audio, but yet can't remember to turn it back on in the first place.  It is a rather annoying problem.  Is there a way to prevent Ubuntu from shutting of the audio during suspend in the first place?

Thanx,

Geo

---

