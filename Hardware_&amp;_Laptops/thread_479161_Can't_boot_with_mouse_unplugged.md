---
title: "Can't boot with mouse unplugged"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Platypi007 on 2007-06-20
Heh, I feel like an idiot making so many posts in one day...

I set up my computer last night to use the thumb buttons of my microsoft intellimouse explorer and added:

     InputDevice "Microsoft Intellimouse" "CorePointer"

to the ServerLayout section of my xorg.conf file.

Today I was unable to start Ubuntu.  After some figuring I realized that the only difference in today and last night is that I do not have the MS Intellimouse plugged in since I'm on the road.  When I commented out the new line out I was able to start up.

I realize this post is possible a bit premature, I should test tomorrow starting up withe the mouse plugged in and the line commented out and see if the thumb buttons still work or not and THEN make this post....

But I may have forgotten where I am with the issue by then and perhaps someone will already know the answer to my problem....

Is there some way to enable the two extra buttons when I'm at home but allow me to still boot without the mouse?

I prefer being able to just unplug everything and go, not have to pack up the mouse and everything...

If I find out tomorrow that I am still able to use the extra buttons I'll delete this post.  Thanks in advance.

---

### Post by yabbadabbadont on 2007-06-20
From the xorg.conf manpage: > Option "AllowMouseOpenFail"  "boolean"
              This allows the server to start up even if the mouse device can&#8217;t be opened/initialised.  Default: false.

You would add this to your ServerLayout section in /etc/X11/xorg.conf

---

### Post by Platypi007 on 2007-06-20
Ah, thanks!  That worked, though I had to rearrange the order of things in the ServerLayout section to make it work but it worked!  Thank you so much!

I'm still learning about using man.  I didn't realize there was a man page for the xorg.conf file.

---

