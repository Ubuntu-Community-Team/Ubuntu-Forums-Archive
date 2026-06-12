---
title: "Help: &quot;No bootable device found&quot; but boots LiveUSB and hard drive can be read"
date: 2015-06-02
forum: Hardware
---

### Post by fcpagdanganan-jr on 2015-06-02
[SIZE=2][FONT=arial]Hi to everyone. My apologies if I'm posting in the wrong place.

I have an Acer V5-131 netbook. I had set it up to dual boot Windows 8 (which was the OS it came with) and Kubuntu 14.04. This set up worked fine until recently. In fact, before I installed Kubuntu I had Ubuntu on it and it also worked fine.

However, just a few days after I installed Kubuntu it gave me the "no bootable device found" message. I don't recall if it was set up to boot in Legacy mode or in EFI mode (I couldn't enter BIOS setup because I couldn't figure out the password).

Anyways, it boots in LiveUSB. And once up, I can see and access my partitions. If it's of any relevance, there's an EFI partition and the partition manager says the disk was formatted in GPT mode.

I've tried reinstalling grub, and when that didn't work, I reinstalled Kubuntu. It didn't work either. I tried boot-repair. I also reinstalled grub-efi-amd64. For a while I thought I succeeded because I got to a grub terminal. But when I issued the command boot I still got the [SIZE=2][FONT=arial]"no bootable device found" message.

Interestingly, the machine booted normally when I did this: I reinstalled Kubuntu from a liveUSB. When installation was completed and I was given the option to continue testing or to restart, I chose restart. I pulled out the liveUSB just as the machine was shutting down prior to a restart. It booted normally showing the grub menu from which I selected "ubuntu."

The machine would never boot normally unless I use this exact same sequence.

Any help will be appreciated. TIA.
[/FONT][/SIZE][/FONT][/SIZE]

---

### Post by kagashe on 2015-06-02
You mean to say that you are installing (or re-installing as you say) Kubuntu from live usb and you can see the grub menu (which is on hard disk since you have removed the usb) and boot. However, you can't boot the next time since you don't see the grub menu. Is it correct?

---

### Post by oldfred on 2015-06-02
With Acer you have to remember password and allow or trust a specific UEFI boot entry to work.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

---

### Post by fcpagdanganan-jr on 2015-06-02
When I boot from a liveUSB I don't get to the Grub menu. After  displaying the Acer logo, the machine boots automatically straight from  the liveUSB. I got to see the Grub menu again when I restart the  computer right after installing Kubuntu from a liveUSB. But the next  time I boot the machine I get the "no bootable device" message.

---

### Post by fcpagdanganan-jr on 2015-06-02
> **oldfred said:**
> With Acer you have to remember password and allow or trust a specific UEFI boot entry to work.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

I'm gonna check these links. However, note that I've had dual-booted Ubuntu with Windows 8 on this machine without any issue. I've also dual-booted Kubuntu without any issue for a while. Then one day I just got this "no bootable device" message. The machine was doing well with Ubuntu-Windows 8 dual-boot set up when I installed Kubuntu. I didn't have to enter BIOS set-up to install Kubuntu. Pardon my ignorance, but could the Kubuntu installation have damaged the EFI partition?

---

### Post by kagashe on 2015-06-03
> **fcpagdanganan-jr said:**
>  I don't recall if it was set up to boot in Legacy mode or in EFI mode (I couldn't enter BIOS setup because I couldn't figure out the password).

Since Windows 8 is working it was not done in Legacy mode. Normally you do not require a password to enter BIOS set up unless the OEM or you set it up. Please read the Manual whether the OEM has set up a password and get it since it is required to solve your problem.

At any time after your purchase did you go for BIOS upgrade or did you give the machine to Service Centre for anything?

> Interestingly, the machine booted normally when I did this: I reinstalled Kubuntu from a liveUSB. When installation was completed and I was given the option to continue testing or to restart, I chose restart. I pulled out the liveUSB just as the machine was shutting down prior to a restart. It booted normally showing the grub menu from which I selected "ubuntu."
It appears to me that the Secure Boot is on in your BIOS and it is remembering Kubuntu as trusted while you restart and showing you the grub menu. After you power off the BIOS forgets that Kubuntu is trusted and fails to boot. The solution to this is to enter the BIOS and try Secure Boot off first then other things suggested like setting a Supervisor password (which is probably already set since you can't enter the BIOS.

> Pardon my ignorance, but could the Kubuntu installation have damaged the EFI partition? No. But an upgraded Kernel may not boot with Secure Boot on.

Kamalakar

---

### Post by fcpagdanganan-jr on 2015-06-03
> It appears to me that the Secure Boot is on in your BIOS and it is  remembering Kubuntu as trusted while you restart and showing you the  grub menu. After you power off the BIOS forgets that Kubuntu is trusted  and fails to boot. The solution to this is to enter the BIOS and try  Secure Boot off first then other things suggested like setting a  Supervisor password (which is probably already set since you can't enter  the BIOS.

@Kagashe Thanks for your reply. Makes a lot of sense. My memory is hazy, but I seem to recall that when I installed Ubuntu to dual-boot with Windows 8 many months ago, I had to change some settings in the BIOS to make the machine boot off a liveUSB and it may have required me to set up a supervisor password which I could no longer remember. Now my problem is how to clear the supervisor password in the BIOS as I don't think I can recall it. Once I've done that, I'll see whether booting with Secure Boot on or off will make any difference.

---

### Post by kagashe on 2015-06-03
> **fcpagdanganan-jr said:**
> @Kagashe Thanks for your reply. Makes a lot of sense. My memory is hazy, but I seem to recall that when I installed Ubuntu to dual-boot with Windows 8 many months ago, I had to change some settings in the BIOS to make the machine boot off a liveUSB and it may have required me to set up a supervisor password which I could no longer remember. Now my problem is how to clear the supervisor password in the BIOS as I don't think I can recall it. Once I've done that, I'll see whether booting with Secure Boot on or off will make any difference.see if this helps [I Forgot My Supervisor Password on My Acer Aspire Mini Laptop 8]("http://smallbusiness.chron.com/forgot-supervisor-password-acer-aspire-mini-laptop-8-35984.html")

I think this one is better [How to reset an Acer BIOS Password]("http://www.tech-faq.com/how-do-i-reset-an-acer-bios-password.html").

Kamalakar

---

### Post by fcpagdanganan-jr on 2015-06-12
UPDATE: I was finally able to boot into Windows 8 (the factory-installed OS) and, later on, install Kubuntu. I don't know the science behind what I did but it worked.

 Here's what I did: Since I can't get into the BIOS due to a forgotten supervisor password, I had to by-pass or clear the password. In an attempt to do so, I opened the the computer and tried to remove, or at least disconnect, the CMOS battery. I didn't know if it was the CMOS battery but it looked like a watch battery by the SD card slot, which was were the CMOS battery was supposed to be. I was not able to remove it as the two leads on either side of it appear to be soldered onto it. I merely raised it from the board. I also removed the harddrive.

After a while I put back everything together again. I turned on the computer and voila! it booted into Windows 8. The BIOS seemed to have reset and reverted to its default settings because I could not boot into a liveUSB and the BIOS no longer asks for a password. Past experience tells me that the computer will not boot from a liveUSB with Secure Boot on. So I entered the BIOS and turned off Secure Boot. I also made the liveUSB first among the list of boot devices. I restarted the computer and it booted off the liveUSB. From there I installed Kubuntu. Thanks to all those who tried to help.

---

