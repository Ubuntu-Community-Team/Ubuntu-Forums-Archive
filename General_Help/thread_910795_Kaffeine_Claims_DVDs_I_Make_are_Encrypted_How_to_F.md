---
title: "Kaffeine Claims DVDs I Make are Encrypted?? How to Fix??"
date: 2008-09-04
forum: General Help
---

### Post by OzzyFrank on 2008-09-04
No... I'm not somehow managing to create my own encrypted/copyrighted titles... and YES, I do already have all "restricted extras" which lets me watch titles in Ubuntu that are in fact commercial and encrypted or copy-protected. But we are talking about video DVDs that I myself have whacked together and burned in GnomeBaker. Totem and other media players that can handle DVDs make no such complaints, but Kaffeine invariably tells me:

[COLOR="DarkRed"]**This DVD Video is encrypted. To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh. In some countries it is illegal to install the decryption software without permission from the video copyright holder.**[/COLOR]

I actually went along with the suggestion once, and ran the LIBDVDCSS install script even though I knew I already had it. Well, technically I suppose I didn't, as this script ignores whatever newer version you have and installs an older version. And that does nothing but makes Update Manager mark it for update, since the new version is replaced by an older one.

I would say that it might have something to do with the fact I use DVD Shrink to whack them together in Windows, but Kaffeine can play most of those I do this way. I would also say I have better luck with those I then burn in Windows rather than Ubuntu, but this isn't conclusive either. Besides, as I've said, other media players can play those "problem" ones without issue, so it definitely is something to do with Kaffeine.

So does anyone know what is going on, and how to fix it? I much rather Kaffeine over the other players, but this situation is slowly changing that. Cheers. Frank

---

### Post by mc4man on 2008-09-05
Kaffeine gives that message pretty much as a generic lib, codec or path error. (or any combination of

Am assumming you can play encrypted commercial dvd's with kaffeine? (if so that implies Kaffeine is ok with a disk with  known correct fs ext's and structure and you have the needed libxine1 codecs

Have you tried having kaffeine access the directory (video_ts) or the mount point vs. the disk? (or from dolphin, open with  

Generally Kaffeine works best when the dvd device in xine engine parameters is set to /dev/scd[COLOR="Red"]x[/COLOR] vs. /dev/dvd ect.

 Unfortunately when using linux burning apps there is always the possibility any particular app doesn't like the way the dvd was created. (in terms of iso creation and or dvd video burning only

(I only use Imgburn for these tasks, never fails to burn including correct extensions and video dvd structure

---

### Post by hyper_ch on 2008-09-05
add medibuntu repos and then install libdvdcss2

---

