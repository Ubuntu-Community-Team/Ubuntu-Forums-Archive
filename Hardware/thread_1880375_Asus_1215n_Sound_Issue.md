---
title: "Asus 1215n Sound Issue"
date: 2011-11-13
forum: Hardware
---

### Post by Alizhdheg on 2011-11-13
Hello.  This is my first post here, so if I do something wrong, please let me know as it is unintentional.

I'm a long-time Windows user who has been struggling to learn Linux.  I've been working off and on it for about 6 months but recently have decided to make a concerted effort to actually make Linux my main OS and run Windows only in a virtual environment (at least on my netbook).

I've run into several issues, but have been able to resolve most (if not entirely all) of them except for this sound issue.  When I first install Ubuntu sound works great.  No issues.

However, after I install Likewise and join the computer to my Active Directory domain, I log in with my AD account and sound appears disabled.  Not muted, but actually disabled.  The sound icon at the top just has three dashes next to it ---.  I can't for the life of me figure out how to resolve this situation.  If I click the icon and choose Sound Settings... nothing is listed under the Hardware tab.

I tried Linux Mint 12 (Lisa) as well.  In that flavor sound didn't work even with the user created during the install.  The symptoms were the same.  The icon showed three dashes and nothing was listed under hardware.

I've searched here and Google for hours and hours trying to fix this.  Unfortunately because the 1215n's most popular issue is the Ion2 compatibility that seems to be the only results I get with my search.  I'm pretty certain this is just a knowledge issue, so if anybody can give me some insight I would be greatly appreciative.

Thank you.

---

### Post by MoreOrLess on 2011-11-13
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Alizhdheg on 2011-11-14
Thank you for the response!

[http://www.alsa-project.org/db/?f=54a677849e8726a905737e78c154a4252e251815](http://www.alsa-project.org/db/?f=54a677849e8726a905737e78c154a4252e251815)

That is the link it gave me.

I feel a bit foolish, but I did all that under the user that is working.  Apparently when I ran updates on Ubuntu 11.10, it broke my install of Likewise so I cannot login using the other account at the moment.

That probably means the report isn't useful for troubleshooting.  If that is the case, please let me know and I can get Likewise fixed tonight when I get home and redo the command.

---

### Post by MoreOrLess on 2011-11-14
Unfortunately(?), the log shows no serious issues. It might be as simple as adding the user to the audio group: [http://www.likewise.com/community/index.php/forums/viewthread/346/](http://www.likewise.com/community/index.php/forums/viewthread/346/)

---

### Post by Alizhdheg on 2011-11-14
I looked at the link you sent and unfortunately appear to be a bit too new to follow the instructions there.

I did, however, add my user to the audio group using sudo adduser *user* audio

This command was successful but unfortunately has not resolved the issue.

---

### Post by dawstones on 2011-11-21
Have you found a resolution to this problem? I have the same issue with a Dell Latitude E6520 with onboard sound.
 
The problem only happens on the likewise windows domain user.

---

