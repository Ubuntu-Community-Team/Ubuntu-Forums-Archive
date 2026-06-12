---
title: "[SOLVED] Downloader for X Adding Extra Slashes / &amp;amp; Can't Fix URLs - Any Ideas?"
date: 2008-08-08
forum: General Help
---

### Post by OzzyFrank on 2008-08-08
About a month or so ago, **d4x** ("**Downloader for X**" or "**WebDownloader for X**") started failing on downloads that were already set up and working, and also on new downloads I added. I soon realised it was adding an forward-slash **[COLOR="Red"]/[/COLOR]** after the main part of the address, ie where the folders begin, and trying to edit this does absolutely nothing. As you can imagine, that's also the reason downloads that were previously working are now failing, as their addresses are getting mutilated with the extra [COLOR="#ff0000"]**/**[/COLOR]. Moreover, it actually gets worse with time, so I can open the program and expect to see the links to look like these or worse (taken from the app, so these aren't exaggerated one bit):

[http://ftp.heanet.ie/////pub/linuxmint.com/5/LinuxMint-5.iso](http://ftp.heanet.ie/////pub/linuxmint.com/5/LinuxMint-5.iso)

[http://ftp.hands.com//////gibraltar/iso-images/gibraltar-2.6.iso.bz2](http://ftp.hands.com//////gibraltar/iso-images/gibraltar-2.6.iso.bz2)

Notice the tilde [COLOR="#ff0000"]**~**[/COLOR] below gets replaced with [COLOR="#ff0000"]**%7E**[/COLOR]:

[http://g3pd.ufpel.edu.br//////////%7Eposeidon/Poseidon_3.0.iso](http://g3pd.ufpel.edu.br//////////%7Eposeidon/Poseidon_3.0.iso)

I've emailed the developer a few times but no response; and the supplied link to his website is invalid. Any ideas what is going on here, and how to fix it if possible. I've gone the whole complete uninstall then reinstall route to no avail.

Also, if you know of an app for downloading that has different speed levels or modes, please share the info. It is the main reason I went with **d4x** over **KGet**, which I was happy with and am using again now. But I'd like to be able to limit the amount of bandwidth the downloader is using, so having 3 handy toolbar buttons available makes that easy. And being able to customise the actual kbps of each mode button (like **d4x**, and **Free Download Manager** in Windows) would be nice. Cheers

---

### Post by OzzyFrank on 2008-12-07
The fix can be found here: [https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368)

There are even reworked .deb files with the fix. This was done by some kind souls as the developer has disappeared totally.

Now I have another problem with urls in d4x: [https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/305915](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/305915) but at least I can add urls properly (just if I add numerical urls, they aren't added, and it wipes the list!).

---

