---
title: "Xubuntu fails with my laptop battery"
date: 2011-07-19
forum: Hardware
---

### Post by aria1121 on 2011-07-19
[FONT=Arial]Hello, everyone on this forum

I am having problems with my Acer Travelmate 630 using Xubuntu 11.04.[/FONT] [FONT=Arial]
After a normal install, it freezes at *Checking Battery State* on first boot. I have searched as hard as possible but didn't find a good solution, so I hope you guys can help me out. In fact I am not so enthustiastic about this since I know the battery doesn't work anymore. It's an old laptop, so I don't see a point to carry it around to need to unplug the powercable.
...when my laptop froze at that moment, I *[Ctrl]+[Alt]+[Del]'d *and on the next boot and all other boots it returns nothing anymore. No splash, no text, just nothing and it stays so.

So, f.e. is there a way to skip [/FONT] [FONT=Arial]*Checking Battery State* on boot?

Thanks,[/FONT] [FONT=Arial]
- aria1121[/FONT]

---

### Post by aria1121 on 2011-07-19
Bump
Sorry guys I really need your help ASAP

---

### Post by aria1121 on 2011-07-20
Bump yet again

---

### Post by aria1121 on 2011-07-20
The **startx** command doesn't help. In the beginning even [Ctrl]+[Alt]+[F1] doesn't work. I have to go to tt2 first to get tt1 work.

Anyone a suggestion?

---

### Post by argument on 2011-07-20
> **aria1121 said:**
> The **startx** command doesn't help. In the beginning even [Ctrl]+[Alt]+[F1] doesn't work. I have to go to tt2 first to get tt1 work.

Anyone a suggestion?

Ok same here. I am stuck on my eeepc 1005/ubuntu with the prompt on Checking battery state... Foolishly I presumed the upgrade would be smooth. Should have waited for the beta :-(

No suggestions from my side.

gRTz

ben

---

### Post by aria1121 on 2011-07-21
Bump
Still waiting for answers. Please, someone overthere *must* have that knowledge how to solve this?

---

### Post by Toz on 2011-07-21
@aria1121, try booting with the **nohz=off** kernel parameter.
Howto: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")
Reference Link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250797]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250797")
If that doesn't work, see below.

@argument, try booting with the **nomodeset xforcevesa** command line parameters. Lets see if its a hardware problem or an X video problem.
Howto: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

---

### Post by aria1121 on 2011-07-21
@ Toz
I have tried to add **nohz=off **but this didn't work (empty screen all the time), and I had some trouble adding **nomodeset xforcevesa**, how do I do this?

Also, I have this written over there (I typed it over from my laptop)

**GNU GRUB  version 1.99~rc1-13ubuntu3**
_______________________________________________________________
[B]setparams 'Ubuntu, with Linux 2.6.38-10-generic'

recordfail[/B] [B]
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f8f585c1-406a-4113-9e68-245ce935e20a
linux /boot/vmlinuz-2.6.38-10-generic root=UUID=f8f585c1-406a-4113-9e68-245ce935e20a ro    quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-10-generic[/B]
_______________________________________________________________

---

### Post by aria1121 on 2011-07-21
(Edited the post ^above^ )

---

### Post by Toz on 2011-07-21
> **aria1121 said:**
> @ Toz
I have tried to add **nohz=off **but this didn't work (empty screen all the time), and I had some trouble adding **nomodeset xforcevesa**, how do I do this?

Follow the instructions at: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

Change your entry > linux /boot/vmlinuz-2.6.38-10-generic root=UUID=f8f585c1-406a-4113-9e68-245ce935e20a ro quiet splash vt.handoff=7
to read:
```
linux /boot/vmlinuz-2.6.38-10-generic root=UUID=f8f585c1-406a-4113-9e68-245ce935e20a ro quiet splash vt.handoff=7 nomodeset xforcevesa
```

and Ctrl+x to boot.

If that doesn't work, retry with just the **nomodeset** entry.

If either of these work, according to the specs I found on the internet,  the 630 has an nvidia video card. Go to System->Additional Drivers and activate any proprietary drivers that might be listed there.

---

### Post by aria1121 on 2011-07-21
Ok, I am now trying **nomodeset xforcevesa**.

---

### Post by aria1121 on 2011-07-21
Nope, didn't work. I had to take out its powercable to get it off.
Now trying nomodeset only.

... Also this leaves an empty screen.
Anything else to do?

---

### Post by aria1121 on 2011-07-21
No wait, after waiting a long time I triggered the on/off button, and suddenly "it came alive"

so yes I guessed it works now.
Just update-grub, right?

---

### Post by aria1121 on 2011-07-21
I remember that when I used Xubuntu 7.10 the Indicator Plugin had a driver which screwed my monitor. I had to reïnstall Gutsy because that was one of the only versions that time that worked...

---

### Post by aria1121 on 2011-07-21
Didn't update grub, but I did update drivers.

What should I do? I feel this is almost solved.

---

### Post by Toz on 2011-07-21
Were there proprietary drivers available? Were those the ones you updated? If so, a reboot should do it now - no kernel parameters should be required.

---

### Post by aria1121 on 2011-07-22
I have reïnstalled Xubuntu, now trying to add **nomodeset** again because previously nothing happened :)

---

### Post by aria1121 on 2011-07-22
Sorry, also, how can I make text appear on startup instead of a quiet boot?

---

### Post by aria1121 on 2011-07-22
- It doesn't work -
I know that Xubuntu boots up, I can even log in, but I can't see anything on the screen. Can't I manually install the driver without booting from the HDD?

---

### Post by Toz on 2011-07-22
Try with the kernel parameter **acpi=off**.
Also see: [http://www.drbloodsvideovault.com/2011/05/linux-mint-on-acer-travelmate-630.html]("http://www.drbloodsvideovault.com/2011/05/linux-mint-on-acer-travelmate-630.html")

---

### Post by aria1121 on 2011-07-23
Ok sorry I'll have to test it later due to some reasons, I'll do it soon..

---

