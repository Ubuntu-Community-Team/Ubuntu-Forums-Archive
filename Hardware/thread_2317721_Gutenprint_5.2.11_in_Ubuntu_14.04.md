---
title: "Gutenprint 5.2.11 in Ubuntu 14.04?"
date: 2016-03-19
forum: Hardware
---

### Post by seanos on 2016-03-19
Is there any way to install the latest version of Gutenprint in 14.04? There isn’t a printer definition for my new Canon Pixma MG7560 in the 14.04 standard repo version (5.2.10-pre2) and building from source seems to produce something that wants to install in /usr/local rather than /usr. But I think I’m in well over my head here.

Should/can the other version be removed first? I’m dubious.

Is there a way of just using the printer definition or is that dependant on the code?

The closest printer models (e.g. MG7100 series, MG8100 series) in 5.2.10 have very different options (e.g. paper trays, etc), so it doesn’t seem like I could use them.

---

### Post by weatherman2 on 2016-03-19
First of all, have you booted something like Ubuntu 15.10 just to see if your printer really is supported in Gutenprint 5.2.11?  If not, no point in wasting your time.

Nothing wrong with installing in /usr/local instead of /usr - I'm pretty sure that's how I built it when I built 5.2.10 from source in Ubuntu 12.04.  /usr/local should take precedence over /usr .  But if you don't like that, you can change the build to go into /usr at the configure step before the build, I believe.  But if you install in /usr/local you won't have to worry about removing the old version - and if you want to back out, you can remove the new version from /usr/local .

---

### Post by weatherman2 on 2016-03-19
FYI, you might try Canon's own Linux drivers - I usually get them from the Canon Europe site.  See if the closest printer to your model's Linux drivers will work in Ubuntu.

Maybe drivers for the MG7550 will work for you:

[http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg7550.aspx?type=drivers&language=EN&os=LINUX](http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg7550.aspx?type=drivers&language=EN&os=LINUX)

---

### Post by seanos on 2016-03-29
I haven’t tried downloading 15.10, installing GIMP and checking if the printer is listed but it is in the [list of supported printers]("http://gimp-print.sourceforge.net/p_Supported_Printers.php").

My problem is that after successfully building version 5.2.11 and installing it the About box for Gutenprint in GIMP still shows 5.2.10-pre2 - 08 March 2014.

> **weatherman2 said:**
> FYI, you might try Canon's own Linux drivers…

The very first thing I did was install the correct Canon driver, but they’re not very good.

---

### Post by mörgæs on 2016-03-30
If you have the space I recommend that you install 16.04 in a dual boot. It contains 5.2.11 by default.

---

### Post by seanos on 2016-03-30
> **mörgæs said:**
> If you have the space I recommend that you install 16.04 in a dual boot. It contains 5.2.11 by default.

That doesn’t sound like a very practical solution (rebooting every time you want to print something). I really don’t need another installation to maintain either, 2 × 14.04 + 1 × 12.04 + Windows 10 (currently broken of course) is quite enough. When 16.04 is stable I’ll upgrade.

The other day I completely removed version 5.2.10-pre2 and reinstalled 5.2.11. GIMP now showed no Gutenprint option, i.e. the plugin wasn’t loading.

I did some more testing and determined that the problem was that the version of Gutenprint built from source installed libraries into [FONT=courier new]/usr/local/lib[/FONT] whereas the Ubuntu version installed them into [FONT=courier new]/usr/lib/x86_64-linux-gnu[/FONT] so GIMP couldn’t locate the libraries needed for the Gutenprint plugin.

The solution I used was to create [FONT=courier new]/etc/ld.so.conf.d/usr-local-lib.conf[/FONT] with this content…

```
# Gutenprint 5.2.11 built from source puts libraries here
/usr/local/lib
```

Then [FONT=courier new]sudo ldconfig[/FONT].

Now GIMP loads the plugin correctly and I can access the right printer options, but there is one downside. Although you can choose print and it appear to print without any error messages, **it does not print**. Printing using the regular print option still works.

How can I diagnose what is happening here?

---

### Post by mörgæs on 2016-04-02
> **seanos said:**
> That doesn’t sound like a very practical solution (rebooting every time you want to print something). 

The idea was to use only 16.04 and reboot to an older install if something should fail. 


> **seanos said:**
> When 16.04 is stable I’ll upgrade.

How do you know if it's stable if you don't try it?

---

### Post by seanos on 2016-04-04
Well, I called the thread Gutenprint 5.2.11 in Ubuntu 14.04, so this is getting a little off-topic, but I&#8217;ll foolishly reply to your post anyway.

Isn&#8217;t up to me what version I install? There are several reasons why I don&#8217;t want to install 16.04 right now, space being one of them, but the fact that every initial release of Ubuntu has bugs, sometimes appalling ones is also compelling and I&#8217;ve made an informed decision that debugging them is not an appropriate choice for me. Reinstalling many, many applications into a temporary beta version of Ubuntu so I could actually do stuff is also unappealing.

This really does seem a desperate waste of pixels. If you can help with getting it working in 14.04 that&#8217;d be great; if you can&#8217;t too bad, but thanks for the interest.

---

