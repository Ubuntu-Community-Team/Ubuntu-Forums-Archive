---
title: "PS3 Help Need!"
date: 2009-02-24
forum: Hardware
---

### Post by Zahne on 2009-02-24
Hi,

I posted this issue on the PSubuntu forums but have not gotten any replies as of yet. If you use PSUbuntu you might know there a few tweaks you need to make. One of them being the resolution change. The tutorial can be found here:

[http://psubuntu.com/forums/viewtopic.php?f=4&t=225&sid=184fd51f63f9dc62d7238cbe9b67659c]("http://psubuntu.com/forums/viewtopic.php?f=4&t=225&sid=184fd51f63f9dc62d7238cbe9b67659c")

I followed the tutorial to the letter and found the right resolution. There's a step on it that makes sure the resolution stays the way you want it to every time you boot:

> Now to make the settings stick everytime you boot, edit your kboot.conf file. 

```

sudo nano -w /etc/kboot.conf


```

Find this line on the end of your boot string..

video=ps3fb:mode:3'

Then change it too the full screen resolution you want to boot with..

video=ps3fb:mode:131'

Now save your kboot.conf *if you are using nano just hit ctrl+x then press Y*




This quote is taken from said tutorial. My only issue is, there is no > video=ps3fb:mode:3' at the end of the boot string. Can I write this line in? Where should I do it? Am I looking in the wrong place? I re-intsalled PSubuntu twice to make sure I didn't accidentally delete it in the first place. That is not the case, it simply isn't here. I'd love help with this as I'm getting tired of adjusting the resolution everytime I boot.

---

### Post by Zahne on 2009-02-25
*Bump* has no one ever heard of this issue? Why is my PS3 the only one that has this issue. I'm two seconds away from selling it, it's becoming more trouble than it's worth.

---

### Post by Zahne on 2009-02-25
actually it may be solved, but I still might sell this thing and get a 64 bit x86 machine.

---

