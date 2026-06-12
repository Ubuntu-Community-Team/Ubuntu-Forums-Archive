---
title: "Lucid boot error"
date: 2010-05-10
forum: Hardware
---

### Post by rossmoore on 2010-05-10
I have a new installation of Lucid on a Zotac Nvidia ION board. It boots fine, but during boot there is a 10 second wait before it displays an error:
nForce2_smbus: Error probing SMB2

Any ideas what's causing this, or how to fix it?

---

### Post by VastOne on 2010-05-10
> **rossmoore said:**
> I have a new installation of Lucid on a Zotac Nvidia ION board. It boots fine, but during boot there is a 10 second wait before it displays an error:
nForce2_smbus: Error probing SMB2

Any ideas what's causing this, or how to fix it?

Search of Google for nForce2_smbus: Error probing SMB2 found this [_[COLOR="Blue"]Here[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+bug/561738")

---

### Post by bluebrave on 2010-05-10
I found a possible solution here:

[http://ubuntuforums.org/showthread.php?t=1435755&highlight=smb2](http://ubuntuforums.org/showthread.php?t=1435755&highlight=smb2) and [http://ubuntuforums.org/showpost.php?p=8570970&postcount=2](http://ubuntuforums.org/showpost.php?p=8570970&postcount=2) 

Here's a summary of instructions:

1. Open a terminal
2. type: sudo gedit /etc/default/grub (going through nautilus only gets you a read only of the file, you will need to edit the file)
3. find the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

Add "acpi_enforce_resources=lax" to that line within the quotes. The line should look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_enforce_resources=lax"

4. Save the file and close
5. Go back to your terminal and type: sudo update-grub

You're done. Reboot

NOTE: I used the above solution and it did work but was more like a band-aid.  
The error was gone on boot but it didn't make boot up any faster (I just got a blinking cursor for 10 seconds before the splash screen - the only difference was that the error message was gone).  I ended up reversing the above step since it wasn't doing any harm and so that as new grub versions come out I can tell which corrected the problem.

*** Update: doing the above did make a difference! 

I started to get a bunch of problems  with Ubuntu having issues with nvidia and wanting to go into  low-graphics mode (also said something about the x server). 

First, I  made sure I had the right nvidia drivers by issuing the command "sudo  apt-get install nvidia-current" (i think that was the command to update  the driver).  Once I did that, I was asked if I wanted to remove some  old files associated with nvidia that were outdated and may conflict.  I  chose yes and the terminal proceeded to do so.

After that, I followed the above steps to get rid of the smb2 stuff and things have worked well since.

---

### Post by rossmoore on 2010-05-10
Thanks guys. I guess I could have googled that myself... obviously a bad day.

---

