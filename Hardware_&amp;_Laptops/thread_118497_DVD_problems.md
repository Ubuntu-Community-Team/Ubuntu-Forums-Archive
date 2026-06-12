---
title: "DVD problems"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by motorbreath on 2006-01-17
Hi All

Have just upgraded to Umbutu from Mandrake and am having problems playing DVDs. When I insert a DVD an icon appears on the desktop but when I try to play it with totem I get this message "Failed to find mountpoint for device /dev/hdc in /etc/fstab". If I try to look at the contents of the DVD I'm told it's blank. 

Audio & data cds work fine and I hade no probs playing DVDs in Mandrake. I have followed all the instructions in the Restricted formats wiki & have tried just about everything suggested on the forums but no luck. 
 
Anyone have any ideas?

---

### Post by bulldogzerofive on 2006-01-17
Ubuntu is free, meaning it only has open-source software included in the default install.  This is not the case in mandrake/mandriva.  You can, however, very easily install this kind of stuff by adding a couple repositories.

First, follow the instructions here to add repositories.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Next, the default multimedia engine in Ubuntu (gstreamer) is not very good at playing DVDs (I don't know why).  In synaptic, install libdvdnav4 and totem-xine (this will uninstall totem-gstreamer).  You should now be able to play most non-region-coded dvds.

In the United States and possibly in other countries, there is no legal way to play region-coded DVDs under linux because it requires decrypting software that is illegal.  There is nothing preventing you from doing this practically, but you are warned.  Personally I don't mess with it.  Read:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)


Good Luck!


EDIT---> Just saw that you already read the wiki... sorry.  Still, I bet you money that if you install totem-xine and libdvdnav4 it will work.

---

### Post by motorbreath on 2006-01-19
Thanks for the info. libdvdnav4 was installed and I did manage to get some success using xine tho playback was choppy & it had a tedancy to just shut down. 

I ended up installing a bucket of stuff using Automatix and DVDs are now working using Mplayer but not totem. Also Nautilus still doesn't recognise the DVD. It displays "DVD-ROM" on the desktop not the title of the DVD. If I open the DVD using Nautilus it thinks it's blank. 

Don't know what that's about but at least DVDs are working :)

---

