---
title: "add XP to Ubuntu/Vista dual boot"
date: 2008-11-06
forum: Hardware
---

### Post by Korijn on 2008-11-06
I intend to add an install of XP onto my notebook: an [Aspire 5930G]("http://acer.nl/public/page9.do?sp=page4&dau34.oid=38481&UserCtxParam=0&GroupCtxParam=0&dctx1=3&CountryISOCtxParam=NL&LanguageISOCtxParam=nl&ctx3=134&ctx4=Nederland&crc=1894738956").

I googled a bit and noticed I would probably have some trouble getting all three to boot. Is there no way to install XP and then re-install grub or something like that?

---

### Post by caljohnsmith on 2008-11-06
Sure, you can add XP to your Ubuntu/Vista dual boot. I think the best way is to make sure you "hide" the Vista partition before installing XP, because there's a chance that XP could put its boot files in the Vista partition; that would not be ideal if you want to keep your OSes independent of each other. To temporarily hide the Vista partition, you can do:
```
sudo grub
grub> hide (hdX,Y)
```
Where (hdX,Y) is the Vista partition in Grub's notation. Once you've installed XP, you can "unhide" Vista with:
```
sudo grub
grub> unhide (hdX,Y)
```
And of course installing XP will overwrite Grub in the MBR, so you'll have to take a few steps to reinstall Grub. That's the general idea, but if you want more specific advice, how about first setting up a primary partition for Windows XP on your computer (it's best not to try to install XP to a logical partition, even though it can be done), and then posting:
```
sudo fdisk -lu

```
And we can work from there if you want.

---

### Post by logos34 on 2008-11-06
[delete-caljohnsmith beat me to it]

---

