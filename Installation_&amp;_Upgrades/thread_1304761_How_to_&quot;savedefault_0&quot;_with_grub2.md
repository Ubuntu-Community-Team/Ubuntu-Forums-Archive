---
title: "How to &quot;savedefault 0&quot; with grub2?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by frafu on 2009-10-29
Hi,


As I only have the pointer to interact with the computer, I used the following procedure to choose what system to boot at startup:

- I set the menu.lst to use the saved value instead of a hardcoded value to identify what entry to boot.

- Before restarting, I tell grub what entry to use for booting with the grub-set-default command.

- Each entry in menu.lst contains a line with the command  "savedefault 0" to reset the saved value to boot from the first entry.


Could anybody please tell me whether something similar is also possible with grub2 and if so, tell me how to set it up?

I tried to find a solution using google, but was only able to find how to use the saved value method to remember the last chosen entry.


By the way, I also found a few pages about enhancing grub2 to support the pointer. Does anybody know whether that feature is already available? It would of course be the ideal solution.


Thanks in advance for an reply.

---

### Post by frafu on 2009-10-31
Hi,

Replying to myself forthe case somebodyhas a similar problem. Here is what I did:

- I disabled 20_memtest86+ and 30_os-prober by doing a "sudo chmod 644" on these files. This way, the menu entries for the other operating systems are not created in grub.cfg

- I manually created the menu entries for the other operating systems in 40_custom and added the following two lines to each entry to reset the value to 0:
saved_entry=0
save_env saved_entry


However, if there is a way to choose the menu entry with the pointer when grub2 shows the menu, that would be better. 


Cheers,

Francesco

---

### Post by madchine on 2010-02-02
Ok, I'm coming at this from a slightly different angle - I just want to use the ability to 'save' a preference manually (grub-set-default) all the while having it reset to ubuntu with each boot.

My solution is, however, pretty similar but perhaps a tad less 'invasive'. The scripts which write grub.cfg use functions in the file **/usr/lib/grub/grub-mkconfig_lib**. So, using root privileges open the file and change the save_default_entry funtion (line 133) to:

```
save_default_entry ()
{
  if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then
    # echo 'saved_entry=${chosen}'
    echo 'saved_entry=0'
    echo 'save_env saved_entry'
  fi
}

```

and run grub-update. Naturally, this file will be overwritten whenever the GRUB packages are updated so personally, I just version lock the grub-common package - otherwise just reapply whenever necessary. Not an ideal solution but until something better comes along... :)

---

### Post by frafu on 2010-02-02
Hi,

It is not necessary anymore to change the permissions of the 30_os_prober file: the same can be achieved by adding GRUB_DISABLE_OS_PROBER=true to /etc/default/grub

Cheers

---

### Post by madchine on 2010-02-04
he, well, we're obviously each going with our different hacks :) Actually I've changed my modus operandi too, feeling that something like this should not just stop working because of an upgrade. 

So, I figured that the one way to make sure it would work on next reboot would be... to change the configuration every time before I reboot - at least if it's needed. 

Here's my 'quitting-Ubuntu-for-a-single-Windows-session' script:
```
#! /bin/bash

sudo grub-set-default "Windows 7 (loader) (on /dev/sda1)"
sudo sed -i s/'${chosen}'/0/g /boot/grub/grub.cfg
sudo reboot


```

[LIST=1]
[*]save windows 7 as the default choice
[*]using sed, edit the grub menu configuration file, so that every menu item saves the first entry as the new default. This way I do not need to edit **/usr/lib/grub/grub-mkconfig_lib** and run grub-update.
[*]restart
[/LIST]
I then added the script to the sudoers file so as not to have to type the password for this to work...

---

### Post by brianafischer on 2010-06-16
> **madchine said:**
> So, I figured that the one way to make sure it would work on next reboot would be... to change the configuration every time before I reboot - at least if it's needed. 

Here's my 'quitting-Ubuntu-for-a-single-Windows-session' script:
```
#! /bin/bash

sudo grub-set-default "Windows 7 (loader) (on /dev/sda1)"
sudo sed -i s/'${chosen}'/0/g /boot/grub/grub.cfg
sudo reboot


```

[LIST=1]
[*]save windows 7 as the default choice
[*]using sed, edit the grub menu configuration file, so that every menu item saves the first entry as the new default. This way I do not need to edit **/usr/lib/grub/grub-mkconfig_lib** and run grub-update.
[*]restart
[/LIST]
I then added the script to the sudoers file so as not to have to type the password for this to work...

Can you post your /etc/default/grub and /boot/grub/grub.cfg files?

---

