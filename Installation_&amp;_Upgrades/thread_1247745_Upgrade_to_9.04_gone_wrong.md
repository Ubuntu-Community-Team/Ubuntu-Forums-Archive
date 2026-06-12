---
title: "Upgrade to 9.04 gone wrong"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by TheWizardofOdds on 2009-08-23
Hi all.

I have been using 8.04 Hardy Heron for a while and decided to upgrade incrementally to 9.04. I downloaded 8.10 from the internet onto disk and installed on my PC no problem. I was asked during install to import my various users and of course, I did. Again, no problem. I then used Upgrade Manager to get 9.04 and wasn't asked about importing different users. The result is that I have only one user now, the root I guess? my girlfriend's account is not recognised nor is my own everyday user account. My emails have vanished also. Naively I imagined that it would all be imported, can I retrieve all my emails and my girlfriends? Do I have to set up the other user accounts again?

Any help would be appreciated, thanks.

---

### Post by zvacet on 2009-08-23
You can create missing users typing in terminal

```
sudo adduser <username>
```

Use your and your girlfriend old usernames.I don´t know about emails.To prevent this to happens in future you can consider making separate home partition.That way all your settings and data/files will be safe.If you want to do it follow [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.

---

### Post by snowpine on 2009-08-23
> **TheWizardofOdds said:**
> Hi all.

I have been using 8.04 Hardy Heron for a while and decided to upgrade incrementally to 9.04. I downloaded 8.10 from the internet onto disk and installed on my PC no problem. I was asked during install to import my various users and of course, I did. Again, no problem. I then used Upgrade Manager to get 9.04 and wasn't asked about importing different users. The result is that I have only one user now, the root I guess? my girlfriend's account is not recognised nor is my own everyday user account. My emails have vanished also. Naively I imagined that it would all be imported, can I retrieve all my emails and my girlfriends? Do I have to set up the other user accounts again?

Any help would be appreciated, thanks.

Hi Wizard, your post is a little confusing... let's try to get to the bottom of what actually happened, shall we?

If I understand correctly, you did not "upgrade incrementally"--you did a fresh install of 8.10, overwriting your existing 8.04 install, and then used the Update Manager to upgrade from 8.10 to 9.04. Is that correct? If so, installing 8.10 on top of 8.04 reformatted the partition and overwrote all of your existing 8.04 data. :(

---

### Post by TheWizardofOdds on 2009-08-24
Thanks for the replies. Sorry if I am clouding the issue here.

Whatever I done I can access 8.04 at the boot menu and having noticed this, I have backed up both of our email settings, messages etc to cd/dvd from the original 8.04. I have then gone in to 9.04 from the boot menu and loaded the disks and restored settings to the new Evolution in 9.04. Now, all seems to be ok except that when I went to send a test email from my girlfriends to mine I am being asked for the SMTP/POP password for [email]username@....on[/email] host, and the message is in the outbox, not sent. I have no idea what the password it's asking me for is? Any thoughts?

---

### Post by TheWizardofOdds on 2009-08-24
Sorted.

The passwords I was being asked for were old ones that I used when my emails were on the internet at my ISP site, and not on my PC.

If I am to upgrade to 9.10 in the future, how do I avoid all this hassle with the emails? Do I have to do a backup and then restore?

---

