---
title: "[SOLVED] Can't Rotate Screen with Compiz"
date: 2008-07-21
forum: General Help
---

### Post by ace214 on 2008-07-21
I have a tablet C running Intel video drivers, and use xrandr to rotate the screen. I recently started using Compiz, but when it is enabled, xrandr causes a freeze. The screen rotates but it doesn't resize. The mouse is then movable but the xrandr terminal line never completes. I have run this with Compiz running in the terminal and it doesn't give any messages after using xrandr.

I would really like to solve this so that I don't have to choose which one to run. I would be open to using another method, but I think my stylus (fpit) rotation is dependent on xrandr, but we'll see.

---

### Post by ace214 on 2008-07-25
Bump...

---

### Post by sloppy shoes on 2008-09-04
I read in another thread (can't find the link right now) that it's a problem with the 3D acceleration and they aren't working on fixing it.

I switched to xfce to get AWN and some of the effects working and rotation works perfectly. I'd just drop compiz, unless there is something you desperately need in it.

I know this isn't that helpful, other than to tell you there is no solution.

---

### Post by ace214 on 2008-09-04
Sorry, I should've marked this thread solved. There's a [bug page]("https://bugs.launchpad.net/mesa/+bug/132065") on Launchpad with a patch for Compiz. But I believe the problem is fixed under Intrepid.

The deb works for me.

---

