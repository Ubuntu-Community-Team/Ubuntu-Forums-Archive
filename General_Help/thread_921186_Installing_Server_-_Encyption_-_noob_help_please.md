---
title: "Installing Server - Encyption? - noob help please"
date: 2008-09-16
forum: General Help
---

### Post by daaussie on 2008-09-16
Hi, just installing ubuntu for first time. I am a noob to this and it has come up with 4 options for "partition disk" in setup.
The following 2 look relevant, do I choose 4
3. Guided - use entire disk and set up LVM
4. Guided - use entire disk and set up LVM with encryption.

Also, I want to set this up as a server for the network, are there any additional encryption programs that I should install?

For example, I found [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix), but this site is well beyond me with too much information to sort through for a novice who doesnt know what he is doing.

Any other useful tips, please let me know.

---

### Post by shaggy999 on 2008-09-16
Be aware that if you choose the option with encryption you will be required to be physically at the machine when it turns on or reboots to enter the encryption password. If you plan to remotely manage the server, I would avoid this option.

---

### Post by bingoUV on 2008-09-16
> **daaussie said:**
> Hi, just installing ubuntu for first time. I am a noob to this and it has come up with 4 options for "partition disk" in setup.
The following 2 look relevant, do I choose 4
3. Guided - use entire disk and set up LVM
4. Guided - use entire disk and set up LVM with encryption.

Also, I want to set this up as a server for the network, are there any additional encryption programs that I should install?

For example, I found [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix), but this site is well beyond me with too much information to sort through for a novice who doesnt know what he is doing.

Any other useful tips, please let me know.

Isn't there an option to use entire disk without LVM? If you are confused by these options, you may not be able to manage the disk with LVM.

Encryption: The data on the disk will be encrypted. You will be asked a password at boot time to so that it can decrypt and boot successfully. You do not need to install any additional encryption programs if you select this. But this may get difficult to troubleshoot for you.

Tips?

1. Do not use LVM unless you know what it means, and what are its advantages.

2. When asking for tips, tell what you expect from a server. Is it a mail server? Any other responsibilities of the server? How many users, and how much is the expected load? How will the users access the server i.e. if mail will they be using IMAP, POP, fetchmail, ssh to the server and check mail locally, any other? What are you limitations as to hardware? Can you afford a $10,000 server? Do you have to run it on an old 286 with dysfunctional floppy drive?

---

### Post by daaussie on 2008-09-16
I chose the encryption,there is no option without LVM as far as I remember.

Details you guys may need to help me further with advice and opinions.

THis will be a cheap server (old desktop) for a small business with 2 people but continuing to grow to 10 in 2-5 years (I hope):
Pentium 4, 1Gb RAM, video card, 60 GB hard drive.

The entire drive will be for installing software programs. 
I am not sure, but as I have hosting that I pay for, this will not run my website.

I presently have networked desktops with:
1. VISTA (350Gb; core 2 duo; 4 months old),
2. XP pro (Pentium 4; ancient), both loaded with the MS Office 07, and 
3. a 3yr old Dell 6000 LAPTOP (XP PRO licenced) which will use OPEN OFFICE - as I cannot be bothered spending more with a further MS Office licence.

They all run off a hub from an ADSL2+ modem, and presently the 4month computer (which I use; -AND- holds all of the business data on it, -AND- is accessed by the other machines) through a networked drive.

So where does the business data go with the UBuntu machine?
1. Possibly a separate 80 GB hard drive (oldish) i have, OR 
2. invest in a new Terabight hard drive (longer life, more memory), OR 
3. a separate hard drive that plugs directly into the network (i.e. the modem or hub), is removal, and separate from the Ubuntu server.

What is our business data?
1. Our files and client files, scans,etc: 

2. Mailserver (not sure what this means?) - I intend for it to run emails (like windows server software does), although alternatively I can still run each computer directly with the 2 MS Office 2007 licences (and outlook)

3. Webserver for CRM access: Again, very new to me. I am going to install APACHE (?) to run SUGAR CRM (havent fully decided on this one yet). I do not have any client management database yet. I want SUGAR (or another) to manage our business lives, and lift all of the client emails from outlook and store them so that outlook files can be simply be cleared to minimize memory storage.

4. Backups: This is critical. Not sure what to do here yet, I can back it up onto one of the networked machines, the above laptop, DVD, take the removal data drive i buy, or a combination, and keep offsite everyday.

---

### Post by cariboo on 2008-09-16
I would suggest setting up a file server using [Samba]("http://us6.samba.org/samba/") to store all your business documents, A 60gb hard drive is going to hold a lot of business files (I just had a look at my own excel directory, 3 years of invoices take less than  400MB). As far as backups are concerned use a minimum of 3 usb keys or external hard drives (this is a business after all, your data is important), always keep at least one off site at all times. Cycle through them one day at the time, that way if there is a failure of your backup devices the oldest one is only two days old.

As far as an email server goes, it would be more cost effective to use your ISP, but get rid of Microsoft Outlook, not because it is Microsoft, but because dealing with the .pst files can be a real pain, start using an email client that is more standards compliant.I have email archived that goes back to 1995, all them are readable with my favorite multi-tool mc, except for the six months that I used Outlook.

For a small company, do you really need customer relations management software, unless you've got a lot of sales people pounding the pavement or working the phones, it is more trouble than it is worth. At my last employer it was hard enough getting the office girl to keep up the service call logs accurately, that if we didn't have paper records of all our calls my income would have been halved.

The one thing I would advise, is that if your are in any type of service business, a good content management system is a god send, it is a good way of keeping track of documentation of what you did on your service calls.

Jim

---

### Post by daaussie on 2008-11-24
Thank you.

In installed it and it works very well. The machine hums instead of sounding like a record player. Windows was beating the machine to death i now know.


The desktop version is excellent, open office, and pdf printing in the open office and as  printer is excellent, not to mention all the programs you can download, the stability, security and low power usage of the software system.

I do run a service based business and have decided to try Sugar crm. It seems quite good, but I want to know the email I should use. Evolution comes standard and looks great with calendar. But it doesn't have a  plugin with SUGAR CRM. I understand Thunderbird does, but I also remember reading a new email program that has just been developed..

Aside from this, I need to resolve the following now:

Open Office "Record" (track changes) doesn't really work as well as in MS Office. It doesnt record the changes on the page so that you can see what is being done

Acrobat isn't loadable on Ubuntu (and i have researched this and found that pdfedit is the best "open" program. But this doesnt allow cropping or to combine several pdfs.

I havent tested my HP and CANON printers

MYOB doesnt install on Ubuntu

KEEP backup (can be installed from "add/remove programs" does not pick up the network drives (or at least I am such an amateur I cant find it).


Overall very happy, and I can't wait till  the upgrades of these programs as i think they will be next to none.

---

