---
title: "Encryption of home folder"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by sebeto on 2009-11-05
Hi everybody!

Today, I just made a fresh install of Ubuntu Karmic (I was on Jaunty).

I've got three partitions:
One for /
One for the swap
One for /home

As I usually do, I told the software to format only / , not /home, so that I could keep all the data in /home

Then, I checked the option to have an encrypted /home folder.

The installation was fine, everything works very well. But I checked by launching the Live CD again, and it appears that my /home folder isn't encrypted. I guess that as it was already there it didn't get encrypted.

Is there any way for me to encrypt it so that it gets unencrypted when I log in, so that it would make the same effect than if it had worked when I installed it?

I know that there are posts about encrypting the /home folder on the forum, but I'd really like to make it as if it had been done on the install. I wanna be sure that I don't do anything bad...

---

### Post by sebeto on 2009-11-05
Any idea guys? :lolflag:

---

### Post by Jenkins1 on 2009-11-05
My suggestion would be copy the unencrypted data to another part-ion or external disk etc. Then do a clean install and copy the info back again.
If you use the -p option on the cp command this will preserve all of the file permissions. Also following these instructions any packages you have installed can be quickly reinstalled. [http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian]("http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian")

---

### Post by sebeto on 2009-11-06
Thank you, I think that I'll do it as you say.

The link about the packages is really great, I didn't know that it was possible to do that, it's really useful!

---

