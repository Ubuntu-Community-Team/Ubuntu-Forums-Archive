---
title: "[SOLVED] Sound very quiet..."
date: 2008-07-12
forum: General Help
---

### Post by chazdraves on 2008-07-12
Well... I'm not sure what happened. I upgraded my GPU and PSU while I was using Windows. Now, I've decided to get into art using GIMP and switched back to Linux only to find that a number of things aren't working as they used to. I have my volume levels all the way up (almost all the way, all the way causes distortion) and I still have to have the volume on my speakers at over half to really hear anything. I'm using an MSI Sli-Fi which I believe is the Realtek 883. It worked fine before... Any ideas?

Thanks, all!
- Chaz

---

### Post by rtcampos on 2008-07-12
> **chazdraves said:**
> Well... I'm not sure what happened. I upgraded my GPU and PSU while I was using Windows. Now, I've decided to get into art using GIMP and switched back to Linux only to find that a number of things aren't working as they used to. I have my volume levels all the way up (almost all the way, all the way causes distortion) and I still have to have the volume on my speakers at over half to really hear anything. I'm using an MSI Sli-Fi which I believe is the Realtek 883. It worked fine before... Any ideas?

Thanks, all!
- Chaz
Try this link:

[http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/](http://weichen.wordpress.com/2007/04/23/upgrade-to-ubuntu-feisty-solve-some-problems/)

This came in handy when I upgraded to Feisty before.  Upgrading to Hardy has the same issue, and the tip suggested also worked!

To quote:

"Then I came across a Chinese article that just solve my problem, and it&#8217;s quite simple! I consider this as a Ubuntu/Linux upgrade bug! Here is the solution:

Type &#8220;gnome-volume-control&#8221; in the terminal. As I am using KDE, there is no icon in my system tray. I need to type the command.

&#8220;Edit&#8221; -> &#8220;Preference&#8221;, check &#8220;Headphone Jack Sense&#8221; and &#8220;Line Jack Sense&#8221;.

Goto &#8220;Switch&#8221; tab, Uncheck both of them. Then you will hear a &#8220;dong&#8221; sound, and the sound is back!
"

---

### Post by chazdraves on 2008-07-12
Interesting... That actually didn't fix it, but I found something while I was looking for those that did. I didn't have the options for sensing on either jacks, but I decided to enable volume controls for all fo the possible things listed. I then started screwing around with the levels one-by-one. PCM has always been my main volume control, but it appears Center and LFE seperately adjust my left and right channels (for whatever reason)... I cranked both of these up and I now have more sound than I know what to do with!

Thanks for pointing me in the right direction!
- Chaz

---

### Post by theudanjoz on 2009-03-20
Wow, that was surprisingly easy and painless. Just typing in the gnome-volume-control popped up the window I needed that I had never seen before in all my efforts of fixing my volume problem. The inline and front volume bars were muted for some reason. I ramped both up just to be safe and now she works like a dream!

Thanks for the link.

---

### Post by TheguywholikesLINUX on 2009-06-04
Wow I can't believe I was so ignorant! my PMC was sitting there with hardly any volume and I had to check it about five or six times before I actually noticed why my sound was soo quiet!!

---

