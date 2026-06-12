---
title: "Ubuntu 11.10 32bit upgrade to 64 bit"
date: 2012-02-01
forum: Hardware
---

### Post by lgabster on 2012-02-01
[FONT="Verdana"](sorry for my bad English)
I want to install 64 bit Ubuntu 11.10, but do not go up the machine, only the 32-bit.
Sandy Bridge CPUs are in my computer, Intel Graphics HD 3000 video card. Maybe this solution can not correctly manage Ubuntu?
[I]Processor: Intel ® Core &#8482; i5-2520 4 × CPU@2.50GHz
Graphics: Mobile Intel ® Sandybridge x86/MMX/SSE2
Laptop: Lenovo Thinkpad L420 [7827][/I]

Otherwise, the cpuinfo flags between lm!
In Google Docs, the following command [FONT="Courier New"]/proc/cpuinfo | grep flags[/FONT]: [http://goo.gl/4ImFc]("http://goo.gl/4ImFc")

What is wrong?
[/FONT]

---

### Post by wolfen69 on 2012-02-02
Did you check the md5sum and verify the cd? I have the same chipsets, (Sandy Bridge) and 64bit ubuntu works great.

---

### Post by lgabster on 2012-02-02
[FONT="Courier New"]zzz@zzz:~$ md5sum -c MD5SUMS
ubuntu-11.10-desktop-amd64.iso: OK[/FONT]

and now?

---

### Post by madvinegar on 2012-02-03
Run in terminal this command and post the results.

```
sudo lshw -C Processor | grep width
```

---

### Post by cbowman57 on 2012-02-03
This is sometimes caused by a problem with the bios, you might want to see if there is an updated bios for your MB.

---

### Post by lgabster on 2012-02-03
> **madvinegar said:**
> Run in terminal this command and post the results.

```
sudo lshw -C Processor | grep width
```

```

    [COLOR="Red"]**width**[/COLOR]: 64 bits

```
(and this is seventeen times)


[QUOTE=cbowman57]This is sometimes caused by a problem with the bios, you might want to see if there is an updated bios for your MB.[/QUOTE]
And where can I find a good version? How do I upgrade?

---

### Post by cbowman57 on 2012-02-03
There should be instructions specific to your motherboard on the same site, or with the bios upgrade.
Could be something else entirely causing your problem but this is where I would start. [http://support.lenovo.com/en_EG/downloads/default.page?](http://support.lenovo.com/en_EG/downloads/default.page?)

---

