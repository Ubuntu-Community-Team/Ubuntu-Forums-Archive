---
title: "What hardware requirements must be met for successful hibernation?"
date: 2022-04-03
forum: Hardware
---

### Post by frankvw on 2022-04-03
On my ancient HP laptop with Ubuntu 12.04 LTS on it hibernation used to work just fine. Since that laptop died and I replaced it with a Dell Inspiron and the then freshly released Ubuntu 18.04 LTS in 2018, I have been unable to hibernate it. I tried [all]("https://askubuntu.com/questions/1031633/enable-hibernate-in-ubuntu-18-04-lts") [the]("https://www.linuxandubuntu.com/home/how-to-enable-hibernate-in-ubuntu-linux") [tricks]("https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html") but, depending on which set of instructions I follow, all I manage to achieve is either a system shutdown, a reboot, Gnome shutting down leaving the system in text mode, an unresponsive system that I then need to power-cycle, or no effect at all.

I also have an ancient Samsung NC10 netbook running Lubuntu 18.04 LTS, which hibernates just fine. As I understand it, under the hood Lubuntu is identical to Ubuntu as far as hibernation is concerned, so Ubuntu itself isn't the problem here.

The problem is that while in suspend mode my current Dell Inspiron drains the battery quite quickly (it barely makes it through the weekend) and routinely suspending the system also wears out the battery much quicker. The battery on my 10 year old Samsung NC10 netbook is currently in better shape than the one on my my less than 4 year old Dell Inspiron.

I understand the security issues involved in hibernating a system using an unencrypted swap file, and the performance penalties associated with encrypting the swap file. I also understand why hibernation is not enabled by default. I'm not complaining about any of that.

What I do want to find out, though, is why hibernation can be made to work successfully on one system but not on another. Obviously hardware capabilities are a major factor here. So my question is: *what is it*, specifically, that allows for successful hibernation on one (laptop) system but prevents it on another? My guess is that the deciding factor(s) are part of the system's power management features, and I also note that hibernation tends to work better on older laptops than on more recent models, but what, exactly, is the deciding factor here?

// FvW

---

### Post by TheFu on 2022-04-04
Lubuntu 18.04 support ended about a year ago. [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

Did you find the "Ubuntu power management" help pages?  Most of the questions above are answered there.
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
[https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate)

And for the current LTS, [https://askubuntu.com/questions/1240123/how-to-enable-the-hibernate-option-in-ubuntu-20-04](https://askubuntu.com/questions/1240123/how-to-enable-the-hibernate-option-in-ubuntu-20-04)

Note how the links provided all have 'ubuntu' in the DNS name?

---

### Post by frankvw on 2022-04-05
> **TheFu said:**
> Lubuntu 18.04 support ended about a year ago. [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)
Correct. However, This is not a support request for Lubuntu 18.04; it is a question on how **U**buntu 18.04 LTS (still supported according to [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)) interacts with power management hardware with regards to hibernation.

> **TheFu said:**
> Did you find the "Ubuntu power management" help pages?
Yes. And various others like it, as per my OP.

> **TheFu said:**
> Most of the questions above are answered there.
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
That page hasn't been updated for twelve years.

> **TheFu said:**
> 
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
Not relevant to hibernation.

> **TheFu said:**
> [https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate)
I'm not looking (nor am I able to) resolve kernel bugs. I'm asking why Ubuntu in general has more problems with hibernation on recent model laptops than on old ones.

> **TheFu said:**
> And for the current LTS, [https://askubuntu.com/questions/1240123/how-to-enable-the-hibernate-option-in-ubuntu-20-04](https://askubuntu.com/questions/1240123/how-to-enable-the-hibernate-option-in-ubuntu-20-04)
Unless in this respect 20.04 is dramatically different from 18.04 (on which I have tried these and many other instructions) my original question remains: what, in general, is the difference in power management hardware between laptops that do and that don't perform hibernation when treated according to these instructions?

> **TheFu said:**
> Note how the links provided all have 'ubuntu' in the DNS name?
Strangely enough, yes, I have. As does "ubuntuforums" which suggests that the hardware category here just might be the correct place to ask these and other questions. But I guess that's just me.

// FvW

---

### Post by TheFu on 2022-04-05
I haven't tried to hibernate in over a decade. Sorry.

But I use standby mode nightly on a laptop.  The only settings I had to touch on my Asus laptop and on a Toshiba and Acer before that was the logind.conf file to ensure the closed lid of the laptop did what I wanted, which is not the default, and to ensure the GigE USB adapter was triggered to shutdown networking and all dependencies.  Basically, since 2013, every laptop I've owned, "just worked" for almost everything.  

When reading the documentation, there seems to be little difference between standby and hibernation. Hibernation takes the RAM contents and dumps them to the swap file, so the swap must be at least the size of RAM on the system. When returning out of hibernation, the swap is read directly into RAM, then brought out of standby to run.

To enter: Running ---> Standby ---> Hibernation
To return: Hibernation ---> Standby ---> Running

The way that HW devices are disconnected/stopped to enter and leave standby seems to be similar to plugging and unplugging USB devices. Some power rules may need to be tweaked to recognize odd hardware.  This seems have more to do with internal devices that don't use USB connections.  

Some motherboards have settings to control power states. I've never touched those on any laptop. On my desktop, I have it return to the power state it was before power loss happened. Generally, by desktops run 24/7/365 and get rebooted based on patch requirements. My desktops are scheduled to do work all times of the day.

My last 3 laptops were installed using UEFI. The prior laptops were legacy boot and I'd always shutdown. I don't know if that matters or not. I'm hardly an expert.  I waited a day hoping someone else would respond to your post. When nobody did, I though it would be better to get some response rather than leave it completely empty. Perhaps I was wrong.

I understand not wanting to submit kernel bugs, but the data the troubleshooting efforts generates might contain the 1 item that is lacking or misconfigured for success.

---

### Post by frankvw on 2022-04-06
> **TheFu said:**
> 
I haven't tried to hibernate in over a decade. Sorry.

But I use standby mode nightly on a laptop.  The only settings I had to touch on my Asus laptop and on a Toshiba and Acer before that was the logind.conf file to ensure the closed lid of the laptop did what I wanted, which is not the default, and to ensure the GigE USB adapter was triggered to shutdown networking and all dependencies.  Basically, since 2013, every laptop I've owned, "just worked" for almost everything.  

When reading the documentation, there seems to be little difference between standby and hibernation. Hibernation takes the RAM contents and dumps them to the swap file, so the swap must be at least the size of RAM on the system. When returning out of hibernation, the swap is read directly into RAM, then brought out of standby to run.

The main difference is that during standby a laptop continues to draw power from the battery (unless plugged in, of course) while during hibernation the system is entirely switched off. As I wrote in my OP, during standby my laptop appears to draw quite a bit of power during standby (it barely makes it through the weekend) and because of the repeated charge/discharge cycles the wear and tear on the battery becomes a problem; standby significantly reduces the battery's service life. Hence my preference for hibernation over standby.

> **TheFu said:**
> 
The way that HW devices are disconnected/stopped to enter and leave standby seems to be similar to plugging and unplugging USB devices. Some power rules may need to be tweaked to recognize odd hardware.  This seems have more to do with internal devices that don't use USB connections.  

Some motherboards have settings to control power states. I've never touched those on any laptop. On my desktop, I have it return to the power state it was before power loss happened. Generally, by desktops run 24/7/365 and get rebooted based on patch requirements. My desktops are scheduled to do work all times of the day.

I use my laptop rather hard, I'm afraid. :P I've got Windows 10 running in VirtualBox most of the time (because the people who pay for my meal ticket require me to support Windoze-only stuff but VB allows me to pause W10 when I don't need it so I can live with it) and I've got a LAMP + Postfix service stack for website development, I usually have Firefox with a dozen of tabs open as well as a bunch of LibreOffice documents, and Thunderbird for email. Starting all that stuff from scratch takes a while, so I simply suspend and only reboot for updates/patches as you do with your desktops. It just makes sense that way.

> **TheFu said:**
> 
My last 3 laptops were installed using UEFI. The prior laptops were legacy boot and I'd always shutdown. I don't know if that matters or not. I'm hardly an expert.  I waited a day hoping someone else would respond to your post. When nobody did, I though it would be better to get some response rather than leave it completely empty. Perhaps I was wrong.

Thank you! I appreciate that. I've been wondering if UEFI could be a factor, but while there are some reports from the field where someone "fiddled with it" and the problem disappeared, these are anecdotal and usually rather vague at best.

> **TheFu said:**
> 
I understand not wanting to submit kernel bugs, but the data the troubleshooting efforts generates might contain the 1 item that is lacking or misconfigured for success.
Agreed! However, I'm not sure I'm looking at a kernel bug here. "Bug reports" that aren't really bugs are a great way to waste the developers' time. I believe this is more a matter of some hardware not playing nicely which may or may not be fixable through proper settings, deep magic or percussive maintenance. ](*,)

I'll keep digging! 

// FvW

---

### Post by #&amp;thj^% on 2022-04-06
> **frankvw said:**
> 

I'll keep digging! 

// FvW
My friend your not alone: [https://www.dell.com/community/XPS/Suspend-and-hibernate-issues-on-XPS-15-9500-on-Linux/td-p/7646809](https://www.dell.com/community/XPS/Suspend-and-hibernate-issues-on-XPS-15-9500-on-Linux/td-p/7646809)
Your title suggests an interest in hardware, All my Lenovo's hibernate T-420 through Legion 5 along with what you've shown to work.(and not work)

---

