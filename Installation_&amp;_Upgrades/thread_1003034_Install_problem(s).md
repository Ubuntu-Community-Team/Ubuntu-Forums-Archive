---
title: "Install problem(s)"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by rdotex on 2008-12-05
I downloaded and burned a CD of 8.04.1 and used the LiveCD several times to be sure everything worked.  In fact, I was very pleased, since my LAN was detected and was accessible, as was the internet.  So, I decided to install it.  This was on a machine that I had been running Linspire for several years, the last was v6.0.

The install took over 2 hours.  Now, when I boot, I get a black screen with the logo and a small bar beneath that goes back and forth for a minute or so, then stops for a couple of minutes and gives me a terminal screen with a lot of data scrolling which stops with the following displayed:

"Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/33e08db3-f6c7-4f31-aa5f-a20b98fa4dd7) = sda3(8,3)
kinit: trying to resume from /dev/disk/by-uuid/33e08db3-f6c7-4f31-aa5f-a20b98fa4dd7
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 No1 tty1

No1 login: "

When I login using my known id and pwrd, I get a fast scrolling screen that stops with a screen full of
"-bash: /dev/null: Permission denied"  followed by
ron@No1:~$

I don't know what to do now.

Any suggestions?

---

### Post by jenkinbr on 2008-12-05
Sounds like you had an installation issue.  Have you tried re-installing to see if this is reproduced?

---

### Post by Therion on 2008-12-05
Almost without exception when I've had an issue like that it's been due to a bad burn of the install media.  I'd suggest you re-burn the install disc and burn it really slooooow (e.g. 2x for a DVD, 16x for a CD).

Also, did you verify the download using the SHA-1 or MD5 Sum?  

I use torrents exclusively any more since every torrent download is self-verifying and eliminates the need for MD5/SHA-1 checks.

---

### Post by rdotex on 2008-12-05
I haven't tried to re-install, since it took so long the first time I was hoping I wouldn't need to do that.

I did verify the md5 of the download.  Burned a CD at 4x and ran the "Check CD for defects" on the CD.  I didn't know how to check the CD otherwise.

Edit:  I did use the BitTorrent for the download.

---

### Post by jenkinbr on 2008-12-05
Could you scan up and down in the terminal window to see if some of the errors generated might give us a clue?  If you spot something questionable, let us know what it says.

hint: ctrl + shift + up/down can be used to scroll up and down through the terminal window

---

### Post by rdotex on 2008-12-05
I tried the 'ctrl+shift+up/down arrows' and 'ctrl+shift+pageup/down' and nothing works!

When done before login, it adds some characters after the cursor, but does absolutely nothing after login.

---

### Post by jack102 on 2008-12-05
hi guys i have just downloaded Ubuntu 8.04 desktop and when i insert the disk into my optical drive i can select the language then i am asked what i would like to do. i highlight install and press enter then an error comes up saying:

I/0 Error
Error reading boot cd


in the top left hand corner some text comes up which is: 204200ef

looking for help. thanks

jack

---

### Post by rdotex on 2008-12-05
Jack:  Please start your own thread!
-----------

Since I was getting nowhere, I decided to try to re-burn a CD at 1x speed and re-install.

I cannot get past the partition screen, no matter what I do, manual or otherwise, it won't go.  Message says that "formatting of swap partition failed" .  I've tried changing everything and no go.

what next?

---

### Post by Therion on 2008-12-09
Sorry...  Wrong thread.

---

