---
title: "Enabling hibernate"
date: 2005-11-21
forum: General Help
---

### Post by jonathanhayward on 2005-11-21
I have an IBM ThinkPad A30 laptop which can go into hibernate, but doesn't wake up. I have a partition which I have set aside to store hibernation pages. It presently formatted as swap, and is slightly larger than my memory + video memory.

Can someone give me the URL to the appropriate HOWTO (or tell me the steps) to get hibernate working?

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail (gmail.com) account, please tell me!

---

### Post by dubz on 2005-11-21
your best bet is to compile it into the kernel. APM + ACPI(might be wrong way round).

thats how i would do it anyway.

do a search on the wiki pages for more info on how to compile a new kernel.

thanks.

---

### Post by psusi on 2005-11-21
[QUOTE=dubz]your best bet is to compile it into the kernel. APM + ACPI(might be wrong way round).

thats how i would do it anyway.

do a search on the wiki pages for more info on how to compile a new kernel.

thanks.[/QUOTE]

You don't need to compile a kernel, the stock ubuntu ones already support it.  And it sounds like the OP has it enabled because he said it hibernates just fine, but won't wake up.  

OP: What exactly do you mean it won't wake up?  Exactly what happens when you boot back up after the hibernate?  Try to be specific.

---

### Post by jonathanhayward on 2005-11-21
[QUOTE=psusi]You don't need to compile a kernel, the stock ubuntu ones already support it.  And it sounds like the OP has it enabled because he said it hibernates just fine, but won't wake up.  

OP: What exactly do you mean it won't wake up?  Exactly what happens when you boot back up after the hibernate?  Try to be specific.[/QUOTE]

What I can remember now is definitely that nothing was restored graphics-wise; I think it gave some text error messages, after a long pause. The error messages said something about pages.

(Sorry for not being specific; network access now involves a song and dance, and I can't be more specific without making a trek. What diagnostics can I provide?)

RELATED BUT DIFFERENT QUESTION: Do the stock kernels include swsusp? Could my behavior (sorry, I don't have it exactly at hand) be explained by my not having added 'resume="/dev/hda3"' to grub.conf?

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail (gmail.com) account, please tell me!

---

### Post by psusi on 2005-11-21
Yes, the stock kernels include swsusp.  I'm not sure if there is supposed to be some sort of auto detection or not, but I went ahead and added the resume= parameter to my kernel command lines.

> **jonathanhayward]What I can remember now is definitely that nothing was restored graphics-wise said:**
> jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail (gmail.com) account, please tell me!

---

### Post by cbudden on 2005-11-21
This wiki page got hibernate working for me (the bit about adding to the kopt line)

---

### Post by jonathanhayward on 2005-11-21
My system doesn't have a grub.conf file, so I'm not sure what to append.

What should I put in a grub.conf file to boot Ubuntu with one big root filesystem on /dev/hda1, the normal swap file on /dev/hda2, and the suspend swap file on /dev/hda3?

---

### Post by jegerjensen on 2005-11-24
I had problems with suspend too, and I couldn't find any grub.conf file either, but here is what I did: (in Breazy)
1) I located a line in /boot/grub/menu.lst reading:
# kopt=root=/dev/sda1 ro 
2) I changed it to:
# kopt=root=/dev/sda1 ro resume=/dev/sda6
3) I ran 
sudo update-grub

Now my suspend works!

Hope this helps

---

### Post by jonathanhayward on 2005-11-24
[QUOTE=psusi]OP: What exactly do you mean it won't wake up?  Exactly what happens when you boot back up after the hibernate?  Try to be specific.[/QUOTE]

It starts what I assume is a hibernate restore, then displays the following, modulo transcription errors:

[4298675.668000] Stopping tasks: ==============================================================|
[4298675.668000] Freeing memory... done (47266 pages found)
[4298766.002000] GTM info 78,3c,0,0,13
[4298771.864000] GTM info 78,14,0,0,13
[4298772.319000] ACPI: PCI interrupt for device 0000.02.00.1 disabled
[4298772.319000] ACPI: PCI interrupt for device 0000.02.00.0 disabled
[4298772.320000] ACPI: PCI interrupt for device 0000.02.15.5 disabled
[4298772.320000] resume: option should be used to set suspend device... swsusp: Need to copy 31176 pages

And then it freezes, although boots normally after being power cycled.

The root filesystem is on /dev/hda1 and the hibernation swap partition I'm trying to use is /dev/hda3 .

Here are the contents of /boot/grub/menu.lst~ and /boot/grub/menu.lst (comments stripped). menu.lst~ has the version I just made; menu.lst appears to have been automatically restored (because of the problems resuming?).

/boot/grub/menu.lst~:

default         0

timeout         3

hiddenmenu

kopt=root=/dev/hda1 ro resume=/dev/hda3

title           Inner Sanctum, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash resume=/dev/hda3
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

Here is menu.lst:


default         0

timeout         3

hiddenmenu

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

Do these diagnostics suggest any obvious problems?

-- 
++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail (gmail.com) account, please tell me!

---

### Post by bissej on 2005-12-06
hello. i am having similar problems getting hibernate to work on desktop. it worked fine under hoary, but with breezy it seems to hibernate okay but then i cannot resume it. i get a bunch of errors when trying to resume, and i need to reboot it. the errors say something like:
-------------------------------------------------------------------------------
IDE device ACPI handler is NULL

resume = option should be used to set suspend deviceswsup

need to copy...

swsup: .....  Highmen interup PCI error
-----------------------------------------
i changed the kopt line to say:
# kopt = root=/dev/hde1 ro resume=/dev/hde5

i think hde5 is the right partition. this is what i get when i do fdisk -l:

/dev/hde1   *           1        2406    19326163+  83  Linux
/dev/hde2            2407        2499      747022+   5  Extended
/dev/hde5            2407        2499      746991   82  Linux swap / Solaris

any ideas?
thanks so much.

---

### Post by eitan on 2005-12-07
i can corroborate the last post.
after doing an apt-get update and updating to kernel-2.6.12-10
hibernate stopped working for me.

editing /boot/grub/menu.lst's kopt line from:

# kopt=root=/dev/hda1 ro

to

# kopt=root=/dev/hda1 ro resume=/dev/hda5

and doing a sudo update-grub

i was able to finally get hibernate working again.

---

### Post by bissej on 2005-12-07
hey. for me, editing the kopt line didn't fix it. as i said in my last post, changing it to:
# kopt = root=/dev/hde1 ro resume=/dev/hde5
didn't help. i then changed it to:
# kopt=root=/dev/hde1 ro pci=noacpi acpi_sleep=s3_bios resume=/dev/hde5
which sort of improved it but not really. with the last of these kopt lines, it gets a bunch of errors when resuming but doesn't die. it eventually boots, but nothing works (for example, i cannot even ping my router.) any ideas?
thanks

---

### Post by eitan on 2005-12-08
i take back my 'corroboration'.  hibernate worked for me once after making the change to the kopt line.  it's been a couple of days and i've had the chance
to attempt hibernate a few more times and it doesn't work.

specifically: i can hibernate the system.  when i try to wake it up, it reads/
loads the pages from memory and once it's done, it appears to output a
couple of lines of text (starting with "GMT .." if i recall porperly) and then
it just hangs there forever.

---

### Post by bissej on 2005-12-12
i've solved the hibernate problem, pretty much. the problem was with how hibernate was being called. instead or calling it from System->Log Out, i call it with (as root):
echo -n "disk" > /sys/power/state
this seems to hibernate it so that it wakes up okay. i recommend jsut doing that.

---

