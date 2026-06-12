---
title: "Hp Zv6000...."
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by Oubipaws on 2005-07-28
Hi Guys, I have been introduced to Ubuntu by a very good friend of mine and I never really had a chance to try it up until recently.  I bought a HP ZV6000 (which by the way, I did read the huge 5 page post on this laptop already) from Circuity City and I love it.  But I'm not much of a PC gamer and I'm not worried about 3D accelleration, but I would love to get Ubuntu installed on my laptop.  

1st Problem.... Install would start and then fail because it couldnt mount the CD again.  I saw the solution on this forum was to burn it to a DVD.  So I have the entire system installed now.  

2nd Problem... Upon booting up, I get to a GDM login screen and all seems well.  As soon as I type in 'oubipaws' or 'root' and try logging in, everything just fails.  How should I go about fixing this?  Is it as simple as NoAcceleration being set?  The same friend who recommended ubuntu said something about passing a 'no interface' line to the kernel through grub?  

I love this little laptop and all I really want is to get linux installed so I can get up and running.  If anyone has had any luck getting this to work, please post :)

Thanks in advance for any help,
-Nick

---

### Post by SymGeosis on 2005-07-29
Oubipaws, the first thing you should do is check out [this](http://zv6000forums.com/viewtopic.php?t=291).

That will get you all up to speed. It is worth pointing out that this isn't for the faint of heart. While none of this is too incredibly difficult for the *nix vetern, new-comers may have a more difficult time.

In answer to your question: the first thing you need to to do set Option "NoAccel" "yes" until you get everything else set up.

Be warned that even though the drivers from ATI drastically improve performance they're still kinda flaky and X may be kinda quirky (nothing horrible, just the occasional problem with the mouse cursor).

Hope this helps.

Edit: You'll also want to enter the following at the command line after you install the driver from the .deb. This will help avoid headaches later on down the road regarding libMesa and friends when upgrading. ```
dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2
```

---

### Post by Oubipaws on 2005-07-29
Hey, thanks for the reply.  I've fairly decent with my linux skills and I've been using Gentoo for almost 3 years, but I wanted to try out Ubuntu.

I got X up and running last night by adding:
"NoAccel"  "True"

Once I was able to actually log in, I had to kill the Gnome session and go back to a command line and reload my touchpad.  I've got to make that automated tonight.  Also it was horribly slow and it was driving me insane.  The 'top' command was showing less than 1% CPU usage though.

---

### Post by SymGeosis on 2005-07-29
Hey, make sure to see my edit at the bottom of the post. I added it right as you were posting.  :)

And judging by your profile you live just down the road from me in Mount Airy...

---

### Post by Oubipaws on 2005-07-29
I actually just moved... I live right in Smithsburg now and work on Ft. Detrick as a computer technician.  I go to school in frederick also though.

This laptop doesn't seem to bad to setup... it's just alot of little configurations :)

---

