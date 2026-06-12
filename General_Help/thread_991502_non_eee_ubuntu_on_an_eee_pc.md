---
title: "non eee ubuntu on an eee pc?"
date: 2008-11-23
forum: General Help
---

### Post by epicbattle on 2008-11-23
Hello, I picked up an eee pc the other day as a laptop, work, whatever pc and I loaded Ubuntu eee onto it. But I kind of don't like it at all... would the SSD that the eee pc has in anyway shape or form effect normal Ubuntu if I were to load it on? Is there any reason why I shouldn't load Ubuntu onto the eee other than the display will be small?

Specs:

Eee 1000 40gig SSD
2 gig ram
1.6ghz

thank you

---

### Post by Gondee on 2008-11-23
The only thing i know of is the EEE pc version has somthings to help the SSD last longer. Thats all i know of. Other than that its a x86 i think, so everything should work fine.

---

### Post by GuitarRocker2562 on 2008-11-23
It will work fine, may requiring some configuration to get wireless or sound working, but it will work.

---

### Post by michaelzap on 2008-11-23
Ubuntu would fly on that Eee PC. It runs just fine on my 4GB 701, including Compiz effects (rotating cube, etc.). Check out forum.eeeuser.com for advice on the best tweaks for your system (in my case, for example, I ran a config script to make everything work well on a small screen and get the wifi working properly, as well as loading a modified kernel that runs faster on my Eee, but stock Ubuntu worked fine).

---

### Post by Tiler on 2008-11-25
I use [ubuntu-eee]("http://www.ubuntu-eee.com/wiki/index.php5?title=User_Guides") and once I disabled the [Remix desktop]("http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Ubuntu_Eee_8.04.1%27s_Regular_Desktop_mode_instead_of_the_Netbook_Remix_interface"), it looks and feels just like Hardy with no heartburn regarding wireless, bluetooth, screen res, etc.  I've spent quite a bit of time getting the configuration the way I like it but for all intents and purposes, it's running Hardy.

eee PC 1000
2gb

---

### Post by snowpine on 2008-11-25
Any version of Ubuntu 8.04 or 8.10 can be made to work on the eee by installing a custom kernel: [http://array.org/ubuntu/](http://array.org/ubuntu/)

This is the same kernel used in Ubuntu eee, so installing Ubuntu 8.04 plus this kernel would be essentially the same thing as disabling the "network remix" interface on Ubuntu eee.

I am using the array.org kernel to run CrunchBang 8.10 on my eee 900ha. Works like a charm! [http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/](http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/)

---

### Post by michaelzap on 2008-11-25
> **Tiler said:**
> I use [ubuntu-eee]("http://www.ubuntu-eee.com/wiki/index.php5?title=User_Guides") and once I disabled the [Remix desktop]("http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Ubuntu_Eee_8.04.1%27s_Regular_Desktop_mode_instead_of_the_Netbook_Remix_interface"), it looks and feels just like Hardy with no heartburn regarding wireless, bluetooth, screen res, etc.

Funny, I went at it the other way around. In installed Ubuntu Hardy and used it for quite a while with the regular Gnome desktop, but just last week I added the Ubuntu Netbook Remix packages to try that out. I'm kind of digging UNR so far, so I think I'll leave it this way for a while (I have a 701, so my screen is smaller).

---

### Post by neu2buntu on 2008-11-25
if you have not already installed the full version of ubuntu on eeepc... format the drive as ext2 not ext3 and this will make the drive last longer.... im running ubuntu 8.10 on acer aspire 1 everything works fine..just had to tweak a bit for wifi.... and sometimes the f11 key is needed to resize an app

---

### Post by HermanAB on 2008-11-25
As on any laptop machine, you should disable the syslog daemon.  That will prevent lots of useless writing to disk.  However, even if you leave syslog running, it is unlikely that you will wear out the SSD in your lifetime.

---

### Post by epicbattle on 2008-11-25
Yup, I disabled the remix desktop and now it works like a charm. Thanks guys.



Have any of you had issues with the wireless configuration not saving the password?

---

