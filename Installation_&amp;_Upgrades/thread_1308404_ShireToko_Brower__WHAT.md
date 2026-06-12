---
title: "ShireToko Brower ?? WHAT ??"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Tom_T on 2009-10-31
Just upgraded from 9.04 using Firefox 3.xxx installed by default.

Now I'm on 9.10 and the browser is ShireToko v3.5.5pre

(Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.5pre) Gecko/20091030 Ubuntu/9.10 (karmic) Shiretoko/3.5.5pre)

Is this right ?? If not how do I remove it and get Firefox back ! ??

Thanks

---

### Post by rbsteinbach on 2009-10-31
Shiretoko is the code-name for the 3.5.x version of FireFox.  You have what you want, but the latest version should come down with on-line update.  Go to the Update Manager & run it...  Best wishes.

---

### Post by macaholic on 2009-10-31
I'm not sure why you have ShireToko installed by default, it's one the preview releases of firefox.
Anyway, you can install normal firefox by going into System>Administration>Synaptic Package Manager, searching for "firefox-3.5" and marking it for installation.

---

### Post by Tom_T on 2009-10-31
Thanks for the replies. Found out why it installed ShireToko.
I had this is my sources.list (not sure how they got in there)

```
## deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic
## deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic
```

So I decided to remove firefox 3.5 using:
> sudo apt-get remove firefox-3.5

That seemed to work..
I then removed the entries from my sources list and reinstalled firefox 3.5 using:
> sudo apt-get install firefox-3.5

All seemed OK, but now I've got SERIOUS problems.

Firefox loads OK (Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.5pre) Gecko/20091030 Ubuntu/9.10 (karmic) Firefox/3.5.4)

But I can't click on any links on a web page.. If I right click and open in new tab, the tab opens fine, but the vertical scroll bar appears on the Left, not the Right..

Scrolling using the track pad is also not working...
So now I have a copy of firefox that can't be used.
(I'm having to post this from IE on a windows machine)

Help...  How do I get a working Firefox ??

Thanks

---

### Post by Tom_T on 2009-10-31
Ok..  Think I may have fixed it !

I ran: 
```
sudo apt-get remove firefox-3.5
```

Then deleted .mozilla from my profile ( I did back up bookmarks, passwords etc)

Reinstalled firefox using:
```
sudo apt-get install firefox-3.5
```

The restored bookmarks, extensions and passwords... seems to be working !!

Please let me know if I did the right thing or missed anything ! :)

Thanks

---

### Post by lovinglinux on 2009-10-31
> **Tom_T said:**
> Ok..  Think I may have fixed it !

I ran: 
```
sudo apt-get remove firefox-3.5
```

Then deleted .mozilla from my profile ( I did back up bookmarks, passwords etc)

Reinstalled firefox using:
```
sudo apt-get install firefox-3.5
```

The restored bookmarks, extensions and passwords... seems to be working !!

Please let me know if I did the right thing or missed anything ! :)

Thanks

Keep in mind that Shiretoko used ~/.mozilla/firefox-3.5 folder for profiles instead of  ~/.mozilla/firefox, which is the one used by the default Firefox, including your new 3.5.4. So you might be using an old version of your bookmarks and settings.

---

### Post by Tom_T on 2009-10-31
Thanks

Before I reinstalled I deleted the entire ~/.mozilla folder.
Then reinstalled bookmarks & passwords etc from backups.

Seems to be working ok. No issues since I've done this ! :)

Cheers

---

