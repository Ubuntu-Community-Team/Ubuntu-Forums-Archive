---
title: "Suspend stopped working on Feisty"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by Námo Mandos on 2008-02-08
I had installed Feisty months ago on my Fujitsu A6020 and suspend/hibernate worked beautifully.  Then, all of a sudden, it stopped.  I don't know what I installed or did to make it stop.

I installed uswsusp and used "s2disk" and "s2both", and all it does is go to a blank screen and then say "suspend: Snapshotting system" and get stuck there.  It does not turn off and has to be forced off by holding down the power button.  It certainly does not resume.

I've read people write about ATI and nvidia graphics drivers.  I am using neither, just an Intel graphics card.  What happened and how can I fix it?

---

### Post by Námo Mandos on 2008-02-08
Oh, and...turning up the loglevel in uswsusp.conf gives error output, but stops at "suspending consoles", where it hangs.  Not very informative.

---

### Post by Námo Mandos on 2008-02-09
bump

---

### Post by Námo Mandos on 2008-02-09
bümp

---

### Post by Námo Mandos on 2008-02-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/190551](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/190551) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can't seem to find anything that specifically matches my problem (since I don't have ATI or nvidia graphics cards), so I filed a launchpad bug, attached.

---

### Post by Námo Mandos on 2008-02-09
Bumpity bump.

---

### Post by Námo Mandos on 2008-02-10
Buuuuump.

---

### Post by astadolfo3 on 2008-04-29
Same identical issue on my laptop: Sony Vaio VGN-SZ450N. Suspend and hibernate worked great on edgy and stop working on gutsy and now hardy. I'm also using a generic Intel graphic so no ATI driver issues. 

Just like above, the s2disk or s2both hang on "suspending console(s)"

Really frustrating! almost considering going back to previous releases since suspend is really important and time saving for me.

Any ideas on what uswsusp is doing while suspending the consoles?

Please help

---

### Post by Námo Mandos on 2008-05-01
You too eh?  It's really hard to find help on this.  People I've talked to suggest upgrading the kernel.  I'm now in a position to do so and hope to upgrade to gutsy soon and perhaps even hardy and maybe that will fix it.

---

### Post by astadolfo3 on 2008-05-03
HI! I already did upgrade to Gutsy and now to Hardy hoping for a solution. No change :(

---

### Post by astadolfo3 on 2008-05-17
Hello,

I got one step forward: finally hibernate works after I did the following (I got from ltorgo user in this forum [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4870020):](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4870020):)

in the /boot/grub/menu.lst file and on the entry of my installation
added a resume option making it look like this:
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fe14f446-7cc3-4f6a-bcde-e4c58ebab4c1 ro quiet splash resume=UUID=0b13b111-429e-4c4a-b93c-8c0f648c6ca2

Obviously you need to put the UUID of your own swap partition. You may get it at the /etc/fstab file

Now I'm still searching for the suspend issue.

It's weird that such a simple tweak would fix the hibernate.

---

### Post by brommage on 2008-05-17
> **astadolfo3 said:**
> 

in the /boot/grub/menu.lst file and on the entry of my installation
added a resume option making it look like this:
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fe14f446-7cc3-4f6a-bcde-e4c58ebab4c1 ro quiet splash resume=UUID=0b13b111-429e-4c4a-b93c-8c0f648c6ca2


Thanks!  This worked like a charm for hibernate.  I still can't get suspend working, though.

---

### Post by astadolfo3 on 2008-05-19
I got finally suspend to work!!! Wow it really feels great since it was a big issue for me. Having to reboot every time I had to move my laptop.

here is what I did (I'm NOT using uswsusp, but just the standard power management delivered with Hardy):

on this file, /etc/default/acpi-support edited as su, I added the module "ptyq4" to the list of modules to be suspended in this position:

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
**MODULES="ptyq4"**

evidently the module ptyq4 was the one that got the suspend and hibernate process stuck. Currently both suspend and hibernate work great!

Try this out and if this does not work there are ways to search for the modules that are preventing suspend.

---

### Post by hvacr on 2008-05-19
I gave both tricks a shot, either one worked for me. Glad they worked for you though.

---

### Post by astadolfo3 on 2008-05-20
> **hvacr said:**
> I gave both tricks a shot, either one worked for me. Glad they worked for you though.

Are you saying that these tricks worked and that you're able to suspend, or do you still have issues?

cheers

---

### Post by hvacr on 2008-05-20
Still have issues.

---

### Post by astadolfo3 on 2008-05-21
Probably the module that is preventing suspend is not ptyq4 in your case. You can try to find which module must be unloaded in your machine before suspend is invoked by following the procedure described [here]("http://wiki.ubuntu.com/DebuggingKernelSuspend?highlight=(suspend)"). 

Then insert the module in the file /etc/default/acpi-support in the location shown on my previous post.

---

### Post by kmorgan54 on 2008-05-29
This thread helped me a lot. I have an ecs gf7100pvt-m that stopped resuming from hibernate. 

It turned out to be either the w83627ehf or coretemp modules. Apparantly it stopped working when I tried to configure sensors and fancontrol.

---

