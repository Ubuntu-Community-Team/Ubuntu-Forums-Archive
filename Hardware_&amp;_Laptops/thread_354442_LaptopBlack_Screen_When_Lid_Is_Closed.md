---
title: "Laptop/Black Screen When Lid Is Closed"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by johnnynojokes on 2007-02-06
I'm a new Linux user, and in love with Ubuntu so far, but a minor bug has been aching me for a while. On my Dell Inspiron 1505, everytime I close the lid the screen goes black, and when I open the lid, the screen stays black, and no mouse movement or typing makes anything better. I have searched the posts for this problem, and done everything but nothing seems to fix this problem. This bug may turn me back to Windows, because part of my lifestyle is moving from place to 
place, and having to restart my computer over and over is aggravating and time consuming. Anyone who can help will save me from a Bill Gates Fate. 

-Thanks!

---

### Post by encompass on 2007-02-06
for the time being this may do for you...
go to your powermanagement settings in System Preferences power management and make it so the screen doesn't shut off when you close the lid.
Could you lookup a link with your specs and post it here?  Or post the details of your graphics card here...
Do you need 3d support.

---

### Post by mr.digwell on 2007-02-08
I am having exactly the same problem with edgy on a dell inspiron 6000 (intel 915 graphics). The funny thing is, I had this problem with mandriva & another distro who's name I can no longer remember about a year ago, but when I tried breezy badger, the problem disappeared! (although I eventually gave up on breezy as I failed to get xvid set up properly for encoding. Frustratingly, xvid/divx is a breeze (no pun) to set up in edgy, but now the laptop lid thing returns. I never tried dapper.) I hope someone has a solution for this as not shutting the lid or restarting is totally impractical. 
BTW I have tried setting power management to do nothing when the lid is closed, but the screen still goes off when I close it.
Please someone help!!

---

### Post by jyotishman on 2007-02-08
Unfortunately, I am having the same problem as well. Whenever the lid of my Dell Inspiron E1405 is closed, the screen goes blank, and I have to resort to nothing but reboot. It is definitely not a very good experience. Has anyone found a solution yet? That'd be great. 

Thanks, 
Jyoti

---

### Post by linux_kid on 2007-02-08
just for the person trying to solve this, this is about intel graphics chips (915) from dell.  I have a 915 series chip without a problem, but i dont have a dell, i have a compaq.

---

### Post by brettr on 2007-02-08
I am running a Dell Inspiron 6000, and i do sometimes get this problem. What i do, and it works most of the time is close the lid for a couple of secs again and then open it.. if it doesn't work, i do it again. I know it might not work for you guys, but it is worth a shot if you have not tried it yet.

---

### Post by jyotishman on 2007-02-10
> **brettr said:**
> I am running a Dell Inspiron 6000, and i do sometimes get this problem. What i do, and it works most of the time is close the lid for a couple of secs again and then open it.. if it doesn't work, i do it again. I know it might not work for you guys, but it is worth a shot if you have not tried it yet.

Yeah, I tried this too -- didn't help. I wonder if this is an issue only with the Dell machines....:confused:

---

### Post by jyotishman on 2007-02-13
Anyone with a solution yet? I came across this post..might be useful; I am yet to try though: [http://ubuntuforums.org/showthread.php?p=1972380](http://ubuntuforums.org/showthread.php?p=1972380)

---

### Post by starlily on 2007-02-15
I had this problem too, I tried a lot of things, but the fix was really simple. 

/etc/acpi/lid.sh is *BROKEN*

I replaced it with a much shorter version I found here on the forums, and all is well. 

There are MANY posts about lid.sh being broken in a lot of ways in Edgy. Will someone who knows how please put a fixed version in the release updates? This was one of the very few things that made my install less than perfect. 

Lily

---

### Post by jyotishman on 2007-02-16
> **starlily said:**
> I had this problem too, I tried a lot of things, but the fix was really simple. 

/etc/acpi/lid.sh is *BROKEN*

I replaced it with a much shorter version I found here on the forums, and all is well. 

There are MANY posts about lid.sh being broken in a lot of ways in Edgy. Will someone who knows how please put a fixed version in the release updates? This was one of the very few things that made my install less than perfect. 

Lily

Cool !!!! I applied the trick mentioned here: [http://ubuntuforums.org/showthread.php?p=1814539](http://ubuntuforums.org/showthread.php?p=1814539)

and it just worked like a charm :-P

Thanks for your help !

---

### Post by mr.digwell on 2007-02-16
> **jyotishman said:**
> Cool !!!! I applied the trick mentioned here: [http://ubuntuforums.org/showthread.php?p=1814539](http://ubuntuforums.org/showthread.php?p=1814539)

and it just worked like a charm :-P

Thanks for your help !


Excellent! Worked a treat for me too.                                   :mrgreen:

---

