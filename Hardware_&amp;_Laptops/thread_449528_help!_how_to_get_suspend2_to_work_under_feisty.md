---
title: "help! how to get suspend2 to work under feisty"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by hughes28105 on 2007-05-20
I have a hp dv6110us laptop with feisty 7.04 with beryl and nvidia 9755 driver. most everything work except hibernate or suspend and having trouble getting suspend2 to work properly. i have search every forum, google, and everywhere else i could find to get suspend 2 tow work under feisty. also tried the travin repository witch has suspend2 recompiled but with no success. i ether get a error message saying that i do not have resume2=swap:/dev/sda1 in my menu.lst file in my boot directory. or i just get the mouse with no login screen. 

 I have a nvidia GeForce Go 6150 with the driver 9755 verison of the nvidia driver installed. used envy to install that driver, feisty 7.04 i compiled the kernel with the original suspend2 patch. the feisty verison of the patch. :(](*,):cry::-k

---

### Post by Kobalt on 2007-05-20
It's Beryl I guess the problem. When I use it, I log out before suspending my computer. If I don't do this, X never recovers from suspending and all I get is a crappy screen and pointer.

---

### Post by reacocard on 2007-05-20
Follow the instructions I set out in this post: [http://ubuntuforums.org/showpost.php?p=2689504&postcount=7](http://ubuntuforums.org/showpost.php?p=2689504&postcount=7)

Beryl works fine with suspend2, it's just a matter of getting it set up.

---

### Post by hughes28105 on 2007-05-20
will this also work with suspend- to-ram as well

---

### Post by reacocard on 2007-05-20
> **hughes28105 said:**
> will this also work with suspend- to-ram as well

No, suspend2 is disk-only. It's very fast and effective once you get it working though, so you probably won't miss suspend-to-ram much (I don't). However, you can do a combined method where it saves everything to disk, but then just goes to sleep. That way it'll resume as quickly as suspend-to-ram, but if you lose power it can still resume from the disk, so you won't lose anything.

---

### Post by hughes28105 on 2007-05-21
how do you get it to work with the nvidia commerical drivers 9755 from nvidia.com. for some resion i put it in hibernate and it does just find but on resume it resets the computer before it finishes resume:(

---

### Post by hughes28105 on 2007-05-21
also how do you get to do a componation of  suspend and hibernation ase you have discribed

---

### Post by reacocard on 2007-05-21
> **hughes28105 said:**
> how do you get it to work with the nvidia commerical drivers 9755 from nvidia.com. for some resion i put it in hibernate and it does just find but on resume it resets the computer before it finishes resume:(

Maybe increase the extra pages allowance?

> **hughes28105 said:**
> also how do you get to do a componation of  suspend and hibernation ase you have discribed

You have to create a new conffile for suspend2 for this, I'll post mine when I get back in a couple days. (no time now, headed out the door :) )

Try this thread for questions in the meantime: [http://ubuntuforums.org/showthread.php?t=284994](http://ubuntuforums.org/showthread.php?t=284994)

---

### Post by hughes28105 on 2007-05-21
how in the world do you increase the paging file allowance

---

### Post by hughes28105 on 2007-05-21
hay i figured out how to increases the page file allowance . now how do i get beryl to work with suspend2. for some reason all i get is a blank screen with a mouse and white box around my mouse.

---

### Post by hughes28105 on 2007-05-21
I figured it out. it's that password screen. for some resion beryl trying to theme it and something blocking beryl from skinning. there need to be some way to tell beryl not to skin the password login screen after resuming and beryl need a way to ignore the password or any other login type screen from being skinned.  now if only there was a way to get Reid of the popping sound that happens every time i put my laptop into hibernate or suspend.

---

### Post by hughes28105 on 2007-05-21
grate now on resume metacity is now running inplace of beryl but beryl manager is saying beryl is still running.

---

### Post by reacocard on 2007-05-22
> I figured it out. it's that password screen. for some resion beryl trying to theme it and something blocking beryl from skinning. there need to be some way to tell beryl not to skin the password login screen after resuming and beryl need a way to ignore the password or any other login type screen from being skinned.

Try changing the 'Unredirect fullscreen windows' option under General Options -> Main -> Advanced in Beryl Settings manager.

---

### Post by hughes28105 on 2007-05-23
Now it works grate. know beryl is working with suspend2 both hibernate and suspend.  Hay thanks!

---

