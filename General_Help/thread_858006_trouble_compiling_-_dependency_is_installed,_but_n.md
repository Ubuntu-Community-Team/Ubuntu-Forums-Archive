---
title: "trouble compiling - dependency is installed, but not recognized"
date: 2008-07-13
forum: General Help
---

### Post by jimmy the saint on 2008-07-13
I am trying to install a newer version of cheese (i know, not the most critical of apps).  ./configure stops and says it needs gnome-doc-utils with a version better than 0.3.something.  This is installed, but I have no idea what I can do to make it be recognized!  I know this is probably a basic issue, but I am just starting to delve into compiling software from source and I figured this would be a good trial run.  Any help would be appreciated.

Thanks

JTS


Oh yeah, I am running Xubuntu 8.04

---

### Post by hyper_ch on 2008-07-13
I guess it needs the -dev package of it

---

### Post by fahadsadah on 2008-07-13
Firstly, it would be easier to install it using apt: **sudo aptitude install cheese**.
Also, post the full error message please, and also attach the configure script.

---

### Post by goldnikevip on 2008-07-13
[www.goldnikevip.com](www.goldnikevip.com)
Do you want to have a comfort shoes to fit your foot?If your answer iscertainly,that please land on our website choose you feel satisfaction's product. Comehere, everyone!Don't scruple ! Our product are popular allover the world with High Quality, Competitive Price, Best Service and Safe Delivery. They are exported to US, UK , Canada , France , Italy ,Germany and many other countries.Sport shoes such as Nike Air Jordan I to XXI and Jordan Dub Zero, NikeShox (R4, R5, OZ, NZ , Turbo, TL1, TL2, TL3 ,TL4, BMW , Classic ,Monster , DE ,VC ),Nike Air max( airmax 90, 95, 97, 2003, 2004, 2005, 2006,TN , TN6),Air Force one, Dunk, James, Kobe ,Adidas , Bape , GUCCI ,ICE CREAM , Timberland , Lacoste shoes and so on.
site:[www.goldnikevip.com](www.goldnikevip.com)
msn : [email]goldnike007@hotmail.com[/email]                
yahoo: [email]goldnike@yahoo.cn[/email]

---

### Post by jimmy the saint on 2008-07-13
Ill try the dev package, then posting the error, but the error is pretty much just saying that the gnome-doc-utils aren't present.  The reason that I am trying a newer version of cheese than the one in the repos is because of the horrible lag of this version that has been reported elsewhere and experienced by me.  Hopefully a newer version will have addressed this.

Just found out there is no dev version.

---

### Post by jimmy the saint on 2008-07-13
here is the last three lines:
```
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... no
configure: error: gnome-doc-utils >= 0.3.2 not found

```

the configure file wont upload though, it says its an invalid file

---

### Post by jimmy the saint on 2008-07-13
figured it out

---

### Post by mc4man on 2008-07-13
Try running this to hopefully fill in what your missing
```
sudo apt-get build-dep cheese
```

edit; no problems building, works with checkinstall so I'd advise you install checkinstall and after the make run 
```
sudo checkinstall --install=yes
``` or install=no if you just want it to build a package to install later.

---

### Post by jimmy the saint on 2008-07-13
so is this a replacement for ./configure?  I thought I had to sucessfuly complete ./configure before I could use checkinstall.  I will give this a shot

---

### Post by mc4man on 2008-07-14
> so is this a replacement for ./configure No not at all
> works with checkinstall so I'd advise you install checkinstall and [COLOR="Red"]after the make run [/COLOR] 

i didn't have any problem running the ./configure and make, though i have alot of libs  and -devs from building other apps.
Did you run the build-dep and try again?
What you posted was the configure file from the source, what's needed is what shows up in the terminal - usually just the last 10 lines or so before an error

---

