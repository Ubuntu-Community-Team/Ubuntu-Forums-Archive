---
title: "sort and grep behaviour changes"
date: 2008-07-26
forum: General Help
---

### Post by vb@vsbe.com on 2008-07-26
Posted this to [gnome], but then found out that KDE behaves the same and could not change the prefix for the previus thread, sorry for cross posting:

I just intalled 8.04 on a laptop

the thing is that some tools transferred from another linux installation don't quite work as expected. here are two most glaring examples:

The old system:

[COLOR="Blue"]mma-k: ~ 89 > cat sample
#

#
# Processor support
#
# CONFIG_6xx is not set
# CONFIG_PPC_85xx is not set
# CONFIG_PPC_8xx is not set
# CONFIG_40x is not set
CONFIG_44x=y
ma-k: ~ 90 > cat sample1
line3
line1
Line2

ma-k: ~ 91 > egrep -v '^(#|\S*$)' ~/sample
CONFIG_44x=y
ma-k: ~ 92 > cat sample1|sort

Line2
line1
line3
ma-k: ~ 93 > egrep -V
egrep (GNU grep) 2.5.1

[snip]
ma-k: ~ 94 > sort --version
sort (GNU coreutils) 5.93
[snip]
[/COLOR]

The new system (8.04):

[COLOR="Green"]pl-p: ~ 188 > cat sample
#

#
# Processor support
#
# CONFIG_6xx is not set
# CONFIG_PPC_85xx is not set
# CONFIG_PPC_8xx is not set
# CONFIG_40x is not set
CONFIG_44x=y
pl-p: ~ 189 > cat sample1
line3
line1
Line2

pl-p: ~ 190 > egrep -v '^(#|\S*$)' ~/sample
pl-p: ~ 191 > cat sample1|sort

line1
Line2
line3
pl-p: ~ 192 > egrep -V
GNU grep 2.5.3
[snip]
pl-p: ~ 193 > sort --version
sort (GNU coreutils) 6.10
[snip]
[/COLOR]


so, the sort on the new system is case insensitive, and regular expression syntax is different - what gives?!

Any hints will be highly appreciated,
tia
/vb

---

### Post by pauper on 2008-07-26
```
[color=green]:~[/color]$ **cat /etc/issue**
Ubuntu 7.10 \n \l

[color=green]:~[/color]$ **egrep --version | head -n 1**
egrep (GNU grep) 2.5.1
[color=green]:~[/color]$ **sort --version | head -n 1**
sort (GNU coreutils) 5.97
[color=green]:~[/color]$ **cat << -1 > ~/Desktop/sample**
> #
>
> #
> # Processor support
> #
> # CONFIG_6xx is not set
> # CONFIG_PPC_85xx is not set
> # CONFIG_PPC_8xx is not set
> # CONFIG_40x is not set
> CONFIG_44x=y
> -1
[color=green]:~[/color]$ **cat << -1 > ~/Desktop/sample1**
> line3
> line1
> Line2
> -1
[color=green]:~[/color]$ **egrep -v '^(#|\S*$)' ~/Desktop/sample**
[color=green]:~[/color]$ **egrep -v '^(#|\s*$)' ~/Desktop/sample**
CONFIG_44x=y
[color=green]:~[/color]$ **cat ~/Desktop/sample1 | sort**
line1
Line2
line3
[color=green]:~[/color]$ **man sort | grep -C 2 WARN**
With no FILE, or when FILE is -, read standard input.

[i]*** WARNING *** The locale specified by the  environment  affects  sort
order.  Set LC_ALL=C to get the traditional sort order that uses native
byte values.[/i]
[color=green]:~[/color]$ **locale**
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
[color=green]:~[/color]$ **export LC_ALL=C**
[color=green]:~[/color]$ **cat ~/Desktop/sample1 | sort**
Line2
line1
line3
[color=green]:~[/color]$ **egrep -v '^(#|\s*$)' ~/Desktop/sample**
CONFIG_44x=y
[color=green]:~[/color]$ **egrep -v '^(#|\S*$)' ~/Desktop/sample**
CONFIG_44x=y
```

Go figure :).

---

### Post by vb@vsbe.com on 2008-07-27
> **pauper said:**
> ```
 $ **man sort | grep -C 2 WARN**
With no FILE, or when FILE is -, read standard input.

[i]*** WARNING *** The locale specified by the  environment  affects  sort
order.  Set LC_ALL=C to get the traditional sort order that uses native
byte values.[/i]

```

Go figure :).

pauper, thank you for the hint, I did get to it too, now I struggled for a while to figure out where the proper place to set the locale is, it is so convoluted, I ended up setting it in a /etc/profile.d script, it sticks! :-)

---

