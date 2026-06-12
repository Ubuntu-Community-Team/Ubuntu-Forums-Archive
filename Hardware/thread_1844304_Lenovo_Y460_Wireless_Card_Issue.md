---
title: "Lenovo Y460 Wireless Card Issue"
date: 2011-09-14
forum: Hardware
---

### Post by Computerfrek on 2011-09-14
Hi, i have got a problem. My wireless card on my Lenovo Y460 Laptop its working in windows but on Ubuntu it shows that it is disabled by hardware switch, i went over the forum one round and found problems like mine but i tired to apply the solution it does not work. Please advise, i know basic linux command but am not fluent in commands regarding hardware. Please Advise thanks :)

---

### Post by TheMiz on 2011-09-14
Some of the XF86 keys on my Y470 work and some do not.  (Actually, only the key that disables the touchpad doesn't work.)  But the key to enable or disable the wireless works perfectly in Ubuntu.  That key is Fn+F5.  

Look at the front center of your computer.  There are four little lights below four little icons.  The icon all the way to the right looks like a little laptop with 2 sets of parenthesis around it.  That is the wireless indicator.  If the light underneath that icon is OFF, your wireless is off and you need to press fn+F5 to turn it back on.

I hope this was the simple fix that you needed.  Anything beyond that is beyond me at this point.

Now if I could just get the graphics card working my Y470 would be UNSTOPPABLE.

---

### Post by Computerfrek on 2011-09-15
But it appears for me my Fn+F5 key does not work on Ubuntu 11.04...

---

### Post by garvinrick4 on 2011-09-20
computerfrek is now online and wishes help with his wireless card and driver
will one of you network guys jump in here and give him a hand.
I have a Network guy I know in these Forums to give you a hand.
There is no reason for me to help right now when better network users are handy.
It was cool to contact me always feel welcome to.

OP is checking on his thread and studing at same time.
 
> I will try to keep online but i am busy studying for my CCNA exam...

---

### Post by garvinrick4 on 2011-09-20
Run this in a terminal and copy and paste the Network controller (wifi card) if you
do not know which one just copy and paste whole thing.
```
lspci -k
```

---

