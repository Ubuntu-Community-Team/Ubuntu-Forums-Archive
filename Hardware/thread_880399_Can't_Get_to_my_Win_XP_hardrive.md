---
title: "Can't Get to my Win XP hardrive"
date: 2008-08-05
forum: Hardware
---

### Post by Nicholas482109 on 2008-08-05
I'm using Ubuntu live CD version 8.04 and i can't figure out how to view the files on the hard drive. Can anyone help?

---

### Post by lisati on 2008-08-05
Do you have NTFS-3G installed?

---

### Post by noobuntu35 on 2008-08-05
> **Nicholas482109 said:**
> I'm using Ubuntu live CD version 8.04 and i can't figure out how to view the files on the hard drive. Can anyone help?

can you see your drive from Ubuntu?

---

### Post by Nicholas482109 on 2008-08-05
I can, it's named 160.0 GB Media

---

### Post by kdb424 on 2008-08-05
Does it ask for a password or what is stopping you from getting on the drive?

---

### Post by Nicholas482109 on 2008-08-05
A window appears saying 
[B]
Cannot mout Volume[/B]
Unable to mount the volume

and another saying

Opening "160.0 GB Media".
You can stop this operation by clicking cancel.

and a third saying

Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I did try to use the command line from information from other websites but that did not seem to work. I could reboot Ubuntu if i need to.

---

### Post by kdb424 on 2008-08-05
That's the information that we needed. I'm not really sure what the problem is. It could be a problem with the CD. I recommend checking that from the first boot menu, and then when you get done with that, someone will probly come up with a better solution if there is one.

---

### Post by noobuntu35 on 2008-08-05
Sorry about not getting back sooner. I searched the Error message and found numerous replies in connection with yours. [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/185756") check this link I believe that they can help you.

---

### Post by noobuntu35 on 2008-08-05
omg I'm an idiot...
here is your answer it's in another forum _you do need to use your CLI_ Its possible you've tried this, rather than link the forum I'll give credit to the poster at the end.
enter this:[FONT="Franklin Gothic Medium"]*sudo mkdir /windows*[/FONT] you'll then need to Mount it[FONT="Franklin Gothic Medium"] *sudo mount /dev/hda1 /Windows*[/FONT]Now the error should disappear.
[FONT="Franklin Gothic Medium"]** You will have to replace the /dev/hda1 with whatever your Windows drive is (It is probably /dev/hda1 or /dev/hda2, or /dev/sda1 or /dev/sda2, depending on your system.[/Font]

Thank you for this Reply posted by rsambuca 9/21/07. in this thread: Accessing Windows files from Ubuntu Live CD.use different wording and the Advanced search option the answers are there. 

I'm not sure that the unmount feature is needed for the live CD or not.

---

### Post by Nicholas482109 on 2008-08-06
I just tried that, hda1 didn't work but sda1 produced this:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /windows ntfs-3g force 0 0

I'm just don't don't know how to use the terminal so i'll wait for a reply on what to do

ubuntu@ubuntu:~$ mount -t ntfs-3g /dev/sda1 /windows -o force
mount: only root can do that

---

### Post by evets25 on 2008-08-06
in order to read a NTFS (windows) partition from ubuntu, windows MUST be shut down cleanly. To make sure, try booting in to windows, then shutting down properly, THEN try booting the live CD again and attempting to mount the drive. If this is just a storage drive, and not the drive windows was actually installed on, then from windows, you need to make sure that you go through the "safely remove hardware" steps to cleanly unmount the hard drive, just like you would to eject a flash drive or other removable device.

---

### Post by noobuntu35 on 2008-08-06
use the command *su root* it will ask for a root password it will be the same as the one you first used when setting up the Live cd you can change the password for root through the main menu> system> administration> users and groups click unlock will ask for your passphrase click on root in the user menu click properties and manually change the password

---

### Post by noobuntu35 on 2008-08-06
> **noobuntu35 said:**
> use the command *su root* it will ask for a root password it will be the same as the one you first used when setting up the Live cd you can change the password for root through the main menu> system> administration> users and groups click unlock will ask for your passphrase click on root in the user menu click properties and manually change the password

put in the command to mount the drive it should work now. sorry it's still new to me too.

---

