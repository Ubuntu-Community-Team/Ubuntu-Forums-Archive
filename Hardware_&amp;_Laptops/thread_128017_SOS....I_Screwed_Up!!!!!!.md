---
title: "SOS....I Screwed Up!!!!!!"
date: 2006-02-10
forum: Hardware &amp; Laptops
---

### Post by caven80 on 2006-02-10
---------------------------------------------------------------------

Quote:
Originally Posted by jonathanm
add uid=[username] into the options of your fstab, where it should read defaults, that should do it 



Hi..

I followed the above quoted method to always be logged on as root and peform any commands without typing da word 'sudo'.

Now i cannot boot into Ubuntu..its giving me some error, so i booted into Ubuntu -recovery mode, and tried to restore the fstab file, which i had backed up earlier, n it says 'Read Only, Cannot Write to File'..

how do i boot in ubuntu now..?

Please Help!!!

---

### Post by Derek Djons on 2006-02-10
Does the SUDO command also not work in the recovery mode?
If the command does work there you can use:

sudo vi "the path"/fstab."file extension"

There you can you use your *insert* key to input and when you are done:

ESC key
: key
then type: wq 
hit the enter key.

---

### Post by caven80 on 2006-02-10
No..the sudo command does not work in da recovery mode..

---

### Post by Derek Djons on 2006-02-10
Damn, sorry... besides that I also don't know anything to overcome this problem.

---

### Post by caven80 on 2006-02-10
Thanks anyway bro...

Can anyone else help me please..or else i will hav to install ubuntu again.
Since i'm dual booting with XP, can i install over the existing linux partition(s) one ext and one swap.

---

### Post by gbw69 on 2006-06-09
[QUOTE=Derek Djons]Does the SUDO command also not work in the recovery mode?
If the command does work there you can use:

sudo vi "the path"/fstab."file extension"

There you can you use your *insert* key to input and when you are done:

ESC key
: key
then type: wq 
hit the enter key.[/QUOTE]

I'm new to linux, but my understanding of the SUDO command is that it runs a command as root when you're logged on as a user.
After boot into the recovery mode it prompts you for a root password for maintenace, you'de be logging on as root then.
Try run the command without SUDO infront of it.

---

