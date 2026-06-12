---
title: "configuring wacom intuos 3 function buttons with fdi file"
date: 2010-07-20
forum: Hardware
---

### Post by KoenHofmeester on 2010-07-20
Hi All,
Quick question: I've looked trough all the wacom threadas on the forums but couldn't find if it is possible to add the function buttons to the linux wacom hal file.

So something like:

<merge key="input.x11_options.*[COLOR="DarkOrange"]PadButton1[/COLOR]*" type="string">*[COLOR="DarkOrange"]key alt[/COLOR]*</merge>

And if so, how do I find out the numerical codes for each pad button? 

Thanks, cheers, 
Koen

---

### Post by Favux on 2010-07-20
Hi KoenHofmeester,

Welcome to Ubuntu forums!

Yes you can use the wacom.fdi.  The format is:
```
<merge key="input.x11_options.OptionName" type="string">OptionValue</merge>
```
so it would be:
```
<merge key="input.x11_options.Button1" type="string">key alt</merge>
```
Here's a button map in post #13:  [http://ubuntuforums.org/showpost.php?p=9517236&postcount=13](http://ubuntuforums.org/showpost.php?p=9517236&postcount=13)

Usually it's done with a xsetwacom script though.  See post #21 on the same thread:  [http://ubuntuforums.org/showpost.php?p=9521493&postcount=21](http://ubuntuforums.org/showpost.php?p=9521493&postcount=21)

The details depend a little on what version of Ubuntu you're using.

Hope this helps.

---

### Post by KoenHofmeester on 2010-07-21
Hey Favux,
thanks for your reply and your welcome...!

im gonna give it a shot!

---

