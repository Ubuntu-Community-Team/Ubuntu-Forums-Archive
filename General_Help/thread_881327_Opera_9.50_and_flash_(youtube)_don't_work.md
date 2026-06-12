---
title: "Opera 9.50 and flash (youtube) don't work"
date: 2008-08-05
forum: General Help
---

### Post by Panthios on 2008-08-05
Hi all.

I have been using Opera for many many years now, and I love it.
I *can't* get used to Firefox. The interface is way to slow compared to Opera.

But Opera freezes when browsing flash sites like Youtube.

Anybody with same problem? The same problem when I was running Debian and Arch Linux. Opera freezes no matter what :(

Right now Im using Adobe Flash 10, grabbed from their website and installed (moved the libflash file) over to .mozilla plugin folder.


Please help. I don't wanna loose Opera, cause in Firefox it works...

---

### Post by carl_pr on 2008-08-05
mmmm with me flash 10 didn't work on opera because it install in 

/.mozilla/plugins

and in my case opera use

usr/lib/mozilla/plugins

what i did is open nautilus as root and paste libflashplayer.so into
usr/lib/mozilla/plugins

it worked for me, i dont know if this is the same thing you are trying to solve, hope it helps.

---

### Post by cybrsaylr on 2008-08-05
I also like Opera the best.

I'm now using Opera 9.51 with no problems on my new laptop. However Flash does not play well on my old PentII PC. Both PCs are running Hardy.

---

### Post by MyR on 2008-08-06
youtube works fine for me in opera 9.51

of course i installed a ton of codecs so i don't know if that has anything to do with it.
sudo aptitude install flashplugin-nonfree libflashsupport

i added a few extensions to firefox to make it work almost exactly like opera.
firefox works better overall, though some things in opera are still superior.

in opera:
click tools > preferences > advanced > content > plug-in options.
there you can see what plugins are being used and what folders are being searched.
i'm using shockwave flash 9.0 r124

peace

---

### Post by Panthios on 2008-08-06
> **carl_pr said:**
> mmmm with me flash 10 didn't work on opera because it install in 

/.mozilla/plugins

and in my case opera use

usr/lib/mozilla/plugins

what i did is open nautilus as root and paste libflashplayer.so into
usr/lib/mozilla/plugins

it worked for me, i dont know if this is the same thing you are trying to solve, hope it helps.

You can define paths in Opera. So your libflashplayer.so could be in /home/user/folder/folder/folder/folder - as long as it is define in Opera.

So this doesnt help me :(

---

### Post by Panthios on 2008-08-06
> **MyR said:**
> youtube works fine for me in opera 9.51

of course i installed a ton of codecs so i don't know if that has anything to do with it.
sudo aptitude install flashplugin-nonfree libflashsupport

i added a few extensions to firefox to make it work almost exactly like opera.
firefox works better overall, though some things in opera are still superior.

in opera:
click tools > preferences > advanced > content > plug-in options.
there you can see what plugins are being used and what folders are being searched.
i'm using shockwave flash 9.0 r124

peace


Just tried aptitude install flashplugin-nonfree libflashsupport and in the Plug-in Options there is standning Shockwave Flash 9.0 r124

But no, I could make Opera freeze by going forward/backwards a couple of times in a video on Youtube..

Just don't understand it.. On THREE different GNU/Linux operations it doesnt work for me, but others, yes.

---

### Post by MyR on 2008-08-06
i'm pretty sure this is a problem with opera, not ubuntu/linux. i'm sure they're working on it...

---

### Post by Panthios on 2008-08-06
> **MyR said:**
> i'm pretty sure this is a problem with opera, not ubuntu/linux. i'm sure they're working on it...


And your right. I have searched around Opera's forum and there a TONS of users who has the same problem..

---

### Post by UbuntuNerd on 2009-09-06
try the fix from this guide:
[http://my.opera.com/ubuntunerd1/blog/how-to-install-opera-web-browser-in-ubuntu-hardy-plugins](http://my.opera.com/ubuntunerd1/blog/how-to-install-opera-web-browser-in-ubuntu-hardy-plugins)

---

### Post by MyR on 2009-09-06
Old thread!

---

### Post by XaversPSP on 2009-11-05
I got the same problem but I got it in Firefox!! In default the Firefox wich comes with Ubuntu is Firefox 3.0 and Youtube and all the other Video sites with FLV or even Mp3 Music doesn't work!! So I give my heart and time on download and installing Firefox 3.5.4 but it still won't work either and I like WT* ?? So i hope maybe someone can help me because for me YouTube is important, very important I must continue doing my videos to keep my subscribers happy. Anyway someone pls help!!

Ubuntu N00b

---

### Post by MyR on 2009-11-05
> **XaversPSP said:**
> I got the same problem but I got it in Firefox!! In default the Firefox wich comes with Ubuntu is Firefox 3.0 and Youtube and all the other Video sites with FLV or even Mp3 Music doesn't work!! So I give my heart and time on download and installing Firefox 3.5.4 but it still won't work either and I like WT* ?? So i hope maybe someone can help me because for me YouTube is important, very important I must continue doing my videos to keep my subscribers happy. Anyway someone pls help!!

Ubuntu N00b

What have you tried so far? Did you install flash?

---

