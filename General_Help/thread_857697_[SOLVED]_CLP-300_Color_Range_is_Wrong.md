---
title: "[SOLVED] CLP-300 Color Range is Wrong"
date: 2008-07-12
forum: General Help
---

### Post by Tybion on 2008-07-12
The printing of photos on the Samsung CLP-300 is VERY poor using the Linux driver (from the Samsung site).  In Windows the result is quite good - so this is not a limitation of the printer hardware.

I have 'CLP-300' selected as the ICM Color Profile.

When I perform a Ubuntu test print this shows various color shades at 0%, 10%, 20% ... 100%.  I will refer to the 'Grayscale', 'Cyan', 'Magenta', 'Yellow' and 'Black' samples on the test printout -

0%, 10% an 20% are all completely white.
70%, 80%, 90%, and 100% are all the same (darkest) shade.

That is, the colour range needs to be stretched out.

How do I do this?

---

### Post by Tybion on 2008-08-07
I found the solution to the poor colour prints from the CLP-300 ..

When I looked in the **/etc/cups/ppd/CLP-300.ppd** file in the ICM section, there was this -

*OpenUI *ICM/ICM Color Profile: PickOne
*FoomaticRIPOption ICM: enum CmdLine A
*OrderDependency: 300 AnySetup *ICM
*DefaultICM: clp300
*ICM clp300/CLP-300: "%% FoomaticRIPOptionSetting: ICM=clp300"
*FoomaticRIPOptionSetting ICM=clp300: "-C10 -G**samclp300-0.icm** "

The last line refers to &#65279;'samclp300-0.icm' but this file did not exist on my system.

Doing a google search on &#65279;&#65279;'samclp300-0.icm' I found out that I could do like so -
```
$ **getweb 300**
samclp300-0.icm
(c) Copyright Samsung 2006
$

```
Presumably this gets the latest version of the file from a Samsung site.  I then copied samclp300-0.icm to -
**/usr/share/foo2qpdl/icm/samclp300-0.icm**
and
/usr/share/foo2zjs/icm/samclp300-0.icm  (probably not required here?)

Now the color profile (as shown by the Ubuntu test print page) is the way it should be.

---

