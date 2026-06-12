---
title: "Thinkpad SL500 Fn keys and harddisk protection"
date: 2009-11-14
forum: Hardware
---

### Post by infestor on 2009-11-14
i just bought a [thinkpad sl 500]("http://www5.pc.ibm.com/dk/products.nsf/$wwwPartNumLookup/_NRJE7MD?open&OpenDocument&epi=web_express") and i use karmic 64bit...how can i enable fn keys to work? so far none of them except the brightness is working...also there is this harddisk shock protection service on windows and wondering if there is such thing possible to enable in ubuntu?

---

### Post by infestor on 2009-11-14
come on guys...no one got it working? :?

---

### Post by mbuller10 on 2009-11-23
try using 32 bit dude

---

### Post by oingk on 2010-01-05
did u get this 2 work, did u try thw 32 bit method?

---

### Post by Whoopie on 2010-01-05
You could follow this howto: [http://wernerroth.de/index.php/2009/12/18/kubuntu-910-runs-a-lenovo-thinkpad-sl500/](http://wernerroth.de/index.php/2009/12/18/kubuntu-910-runs-a-lenovo-thinkpad-sl500/)

The main part is to load the lenovo-sl-laptop kernel module.

For HDD protection, you need the the hdapsd package. But as mentioned [here]("http://github.com/tetromino/lenovo-sl-laptop"), the lenovo-sl-laptop doesn't support the hdaps accelerator. And you can't use the hdaps kernel module as the SL 500 is not a "real" thinkpad.

Some interesting links:
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/434568](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/434568)
- [http://www.thinkwiki.org/wiki/Category:SL_Series](http://www.thinkwiki.org/wiki/Category:SL_Series)

---

### Post by oingk on 2010-01-05
whoopie, thanks very much for this

---

### Post by infestor on 2010-01-12
> **Whoopie said:**
> You could follow this howto: [http://wernerroth.de/index.php/2009/12/18/kubuntu-910-runs-a-lenovo-thinkpad-sl500/](http://wernerroth.de/index.php/2009/12/18/kubuntu-910-runs-a-lenovo-thinkpad-sl500/)
thx for the link...i got all working except fn+f8 (ultranav/touchpad selector)...any got that one working?
as for the HDAPS, i guess no one got it working :(

---

### Post by infestor on 2010-03-09
anyone got **fn+f8** *(ultranav/touchpad selector*) working?

---

### Post by cinecek on 2010-04-23
This worked form me (using SL500, Ubuntu Karmic).
[http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/](http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/)

---

### Post by infestor on 2010-05-11
> **cinecek said:**
> This worked form me (using SL500, Ubuntu Karmic).
[http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/](http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/)

well that does not work in lucid. and by 'not work' i mean the selector ( fn+f8 ) and ejector (fn+f9) do *not* work :(

---

