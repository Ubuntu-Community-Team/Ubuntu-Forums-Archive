---
title: "[SOLVED] kubuntu hardy no boot screen"
date: 2008-05-04
forum: Hardware
---

### Post by oliwally on 2008-05-04
I've installed Kubuntu 8.04 on my Dell D820. All works well by default with only minor tweaking needed. I installed the Nvidia drivers using kubuntu (not envy) and it's rockin' along just fine. Compiz desktop effects work well.

Minor problem now is that when booting, I'm not seeing the kubuntu boot screen loading bar thingo. It just shows a black screen until the logon screen appears. It's no big deal, just would be nice if it worked like it's supposed to.

Is this a common problem with a known fix?

---

### Post by oliwally on 2008-05-07
> **oliwally said:**
> I've installed Kubuntu 8.04 on my Dell D820. All works well by default with only minor tweaking needed. I installed the Nvidia drivers using kubuntu (not envy) and it's rockin' along just fine. Compiz desktop effects work well.

Minor problem now is that when booting, I'm not seeing the kubuntu boot screen loading bar thingo. It just shows a black screen until the logon screen appears. It's no big deal, just would be nice if it worked like it's supposed to.

Is this a common problem with a known fix?

Any ideas anyone?

---

### Post by andyrue304 on 2008-05-07
> **oliwally said:**
> Any ideas anyone?

I don't know if this will help or not but I was having a problem with the Kubuntu splash screen (it was displaying this instead of the ubuntu splash)

I fixed this by using ```
sudo apt-get remove kubuntu-artwork-usplash kubuntu-default-settings
``` which removed the Kubuntu splash screen.

Maybe you can use the synaptic package manager to mark kubuntu-artwork-usplash and kubuntu-default-settings for reinstallation?

---

### Post by locosmurf on 2008-05-07
> **oliwally said:**
> I've installed Kubuntu 8.04 on my Dell D820. All works well by default with only minor tweaking needed. I installed the Nvidia drivers using kubuntu (not envy) and it's rockin' along just fine. Compiz desktop effects work well.

Minor problem now is that when booting, I'm not seeing the kubuntu boot screen loading bar thingo. It just shows a black screen until the logon screen appears. It's no big deal, just would be nice if it worked like it's supposed to.

Is this a common problem with a known fix?

It sounds to me like your resolution is set higher than different than the splash screen is made for. Try setting it to 1024x768 and see if that fixs the problem.

---

### Post by oliwally on 2008-05-17
> **andyrue304 said:**
> 
Maybe you can use the synaptic package manager to mark kubuntu-artwork-usplash and kubuntu-default-settings for reinstallation?

I did this but to no avail.


[QUOTE=locosmurf]
It sounds to me like your resolution is set higher than different than the splash screen is made for. Try setting it to 1024x768 and see if that fixs the problem.[/QUOTE]

That's possible, but I like my screen resolution as it is (1920 X 1200). If I wanted to, how would I change this for the booting sequence? Doesn't that sort of stuff load a little later when X kicks in? Also, when I had Gutsy running the booting screen loading bar thingo worked.

Furthermore, when I use the hardy desktop cd to run kubuntu (to try kubuntu out so-to-speak), then the loading scroll bar works. After loading kubuntu the resolution is in fact 1920 X 1200 by default that way.


Hmmm... I'm stuck. Any other suggestions please?

---

### Post by locosmurf on 2008-05-21
well that is interesting.... have you tried messing with the grub config file? I don't know how much you know about this and I'm currently not at my computer to help with this but as soon as I get the interweb back on my desktop I can login and help more :)

And sorry about not getting back to you sooner. Like I said, I currently don't have the interweb hooked up.

---

### Post by oliwally on 2008-05-25
Thanks locosmurf. I may know a little about the grub menu.lst. I'm looking forward to any further light you may be able to shed on my problem.

---

### Post by editrix on 2008-06-15
Hello oliwally:

Have you managed to fix this? Because I have the same problem, only on a PC. There's a lot about this bug on Launchpad, but for Gutsy. 
[https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930)

I can't find anything about it for Hardy.

---

### Post by oliwally on 2008-06-16
> Have you managed to fix this? Because I have the same problem

No, I haven't found a solution yet. Still waiting for someone clever to help out.

> There's a lot about this bug on Launchpad

Thanks for that, I didn't know. I'll have to have a look at it.

---

### Post by oliwally on 2008-07-16
I have found a solution that worked for me (found at the above mentioned launchpad link)

There bluwShark wrote:

> 1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /etc/boot/menu.lst
3) sudo update-initramfs -u -k `uname -r`

I found the fix at [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558)

Although I didn't have to do step 2 - it worked without that.

---

