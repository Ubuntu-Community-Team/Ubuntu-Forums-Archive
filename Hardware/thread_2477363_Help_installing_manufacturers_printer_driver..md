---
title: "Help installing manufacturers printer driver."
date: 2022-07-22
forum: Hardware
---

### Post by joey1990 on 2022-07-22
Hi,
I'm struggling to install some drivers for a thermal printer? The manufacturer claims that its compatible with Linux, but doesn't supply a PPD file and gives no instructions. 
In the reviews of the printer someone said they've got it working and that the driver supplied is a binary self extracting shell script. I have no idea what that is. There is no file extension which is weird.
Can anyone help please?


This is the printer [https://www.amazon.co.uk/gp/product/B099PPP5FW/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B099PPP5FW/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1)

I've added some screen grabs if that helps.

---

### Post by guiverc on 2022-07-22
> **joey1990 said:**
> Hi,
In the reviews of the printer someone said they've got it working and that the driver supplied is a binary self extracting shell script. I have no idea what that is. There is no file extension which is weird.
..
I've added some screen grabs if that helps.

You haven't provided any release details; but if you're using a default wallpaper; that looks like [Lubuntu 21.10 which is EOL]("https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/") as are [Ubuntu 21.10 & all *flavors*]("https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/"). It could also be you're using a later release, and selected that wallpaper as you like it in which case you'll be okay.

I downloaded that file, and it matches what "*somewhat*" reported..  Firstly I asked my system what I'd downloaded (ie. asking it to *peak* inside the file and report what it finds)

```
[FONT=monospace][COLOR=#54ff54]**guiverc@dc780-deb**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Downloads**[/COLOR][COLOR=#000000]$   file Label\ Printer\ Driver\ For\ Linux  [/COLOR]
Label Printer Driver For Linux: data
[/FONT]
```

Alas '*data*' doesn't tell me much, so then I used 

```
[FONT=monospace][COLOR=#54ff54]**guiverc@dc780-deb**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Downloads**[/COLOR][COLOR=#000000]$   view Label\ Printer\ Driver\ For\ Linux [/COLOR]
[/FONT]
```

and sure enough I can see the  the script at the top as the other person no doubt saw, being

```
line=`wc -l $0|awk '{print $1}'` 
line=`expr $line - 8` 
tail -n $line $0|tar xj -C /tmp 
cd /tmp 
chmod 777 setup 
./setup 
ret=$? 
exit $ret 

```

followed by a large scary *binary blob* (*tarball*) that no doubt lead to the system reporting it as "*data*".

The code is *obfuscated*, but it removes the top 8 lines & leaves you with a tarball which contains many PPD files, a couple of other files and a setup shell script too.

This may not be what's need to help you install, but I'd firstly check what release you're using, as my first indication from your provided wallpaper is you're using an *end of life* release (*it looks like a 21.10 wallpaper to me*).

---

