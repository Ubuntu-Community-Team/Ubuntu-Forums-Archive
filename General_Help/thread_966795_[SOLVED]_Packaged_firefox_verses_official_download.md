---
title: "[SOLVED] Packaged firefox verses official downloaded firefox"
date: 2008-11-01
forum: General Help
---

### Post by n0manarmy on 2008-11-01
I use an application for my online classes called webtycho that requires java to function. In a fresh install of 8.04 I was able to access webtycho without any problems but with a fresh install of 8.10 I'm not able to fully access the site. I can log in but I get the error message 

*JavaScript 1.5 or higher is required for use with WebTycho. Please click Refresh/Reload for upgrade information and follow the instructions.*

When I downloaded the official release from Mozilla's website I'm able to access the classes just fine.

There's been quite a few threads with previous versions that talk about [java plugin]("http://ubuntuforums.org/showthread.php?t=810983") this and [jre download]("http://ubuntuforums.org/archive/index.php/t-220311.html") that but none of them have worked for me.

My biggest question is why does it work with the official downloaded firefox 3.03 version directly from Mozilla's website and NOT with Ubuntu's Firefox 3.03.

It can't be plugins because there's no java plugins installed with the fresh version, I haven't linked any and it shouldn't be able to access sun-java6 which I have installed.

---

### Post by Nepherte on 2008-11-01
All I know is that javascript is handled by the browser itself and not by a java virtual machine. So you can indeed forget about jre and java plugin as you suspected already. I suppose there might have slipped a bug into it while packaging firefox or xulrunner.

---

### Post by n0manarmy on 2008-11-06
> **Nepherte said:**
> All I know is that javascript is handled by the browser itself and not by a java virtual machine. So you can indeed forget about jre and java plugin as you suspected already. I suppose there might have slipped a bug into it while packaging firefox or xulrunner.

Well if it's the chance that it's a bug that was included with the firefox that was packaged with ubuntu, is there an easy way to replace the integrated firefox with the release from mozilla's website and keep the ability for the plugins installed through synaptic working?

---

### Post by OrangeCrate on 2008-11-06
> **n0manarmy said:**
> Well if it's the chance that it's a bug that was included with the firefox that was packaged with ubuntu, **is there an easy way to replace the integrated firefox** with the release from mozilla's website and keep the ability for the plugins installed through synaptic working?

If you remove "ubufox" through Synaptic, you'll have a clean Firefox install.

**Ubufox package description...**

> Ubuntu Firefox specific configuration defaults and apt support. Extension package for Firefox provides Ubuntu specific configuration defaults as well as apt support for firefox plugins/extensions. **You can uninstall this package if you prefer to use a pristine Firefox install.**

---

### Post by jamesstansell on 2008-11-07
> **n0manarmy said:**
> 
It can't be plugins because there's no java plugins installed with the fresh version, I haven't linked any and it shouldn't be able to access sun-java6 which I have installed.

What does [http://browserspy.dk/java.php](http://browserspy.dk/java.php) show in each of the browser versions?

Your fresh install of 8.10 will have openjdk6 set as the default jvm and icedtea6-plugin as the default mozilla java plugin.  When you installed sun-java6 it may not have deactivated that.  So instead of playing a "should/shouldn't" mindgame it's good to check what the browser is actually doing.

The javascript message is really weird. Java 6 added a built-in javascript interpreter, and both the sun-java6-plugin (plugins since there are 2 to choose from in 6u10) and the icedtea6-plugin packages include java <--> javascript connections, but neither of those sounds related to the message that you are getting.

---

### Post by n0manarmy on 2008-12-04
The issue's resolved. The problem is that Ubuntu incorporates Javascript 1.4 in their releases of firefox and this causes havoc with webtycho.

I went over to [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) and grabbed their updater for firefox which installed the latest version of firefox along with migrating my profile successfully and will continue to update for me.

---

### Post by jamesstansell on 2008-12-04
> **n0manarmy said:**
> The issue's resolved. The problem is that Ubuntu incorporates Javascript 1.4 in their releases of firefox and this causes havoc with webtycho.

I went over to [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) and grabbed their updater for firefox which installed the latest version of firefox along with migrating my profile successfully and will continue to update for me.

Glad to hear you got it worked out.

Where did you find out the thing about javascript 1.4?  That's not sounding familiar to me.

Regards,

-james.

---

### Post by n0manarmy on 2008-12-05
> **jamesstansell said:**
> Glad to hear you got it worked out.

Where did you find out the thing about javascript 1.4?  That's not sounding familiar to me.

Regards,

-james.

I've been browsing around about this problem for over a year now and the biggest confusion I can think is that people assume that Java is only the Java Release Engine from [www.java.com](www.java.com). This doesn't appear to be the case with this particular issue. There's an additional component of Firefox that handles java script, where or how that component is compiled or accessed I don't know.

***If you take your browser and point it to [http://webtycho.umuc.edu](http://webtycho.umuc.edu) and at the bottom of the page you'll see a box labeled "Check Your Browser." ***

With the included firefox I get that javascript 1.4 is installed and webtycho requires 1.5.

With the download directly from Mozilla's website I get javascript 1.5 and it works fine.

Attached are the screen shots of the report

EDIT:

The left image is the included version in Ubuntu and the right image is the one directly from Mozilla's website

---

### Post by jamesstansell on 2008-12-05
> **n0manarmy said:**
> I've been browsing around about this problem for over a year now and the biggest confusion I can think is that people assume that Java is only the Java Release Engine from [www.java.com](www.java.com). This doesn't appear to be the case with this particular issue. There's an additional component of Firefox that handles java script, where or how that component is compiled or accessed I don't know.

***If you take your browser and point it to [http://webtycho.umuc.edu](http://webtycho.umuc.edu) and at the bottom of the page you'll see a box labeled "Check Your Browser." ***

With the included firefox I get that javascript 1.4 is installed and webtycho requires 1.5.

With the download directly from Mozilla's website I get javascript 1.5 and it works fine.

Attached are the screen shots of the report

EDIT:

The left image is the included version in Ubuntu and the right image is the one directly from Mozilla's website

Thanks.  Now I see what you mean.

Wow - I had a look at their code and it's pretty scary.  (Not the worse I've ever seen though.)

They're not checking javascript versions the recommended way.  Instead using some spaghetti logic based on browser name.

My first guess is that the difference in the user agent string is confusing their spaghetti.

You can tell from [http://browserspy.dk/javascript.php](http://browserspy.dk/javascript.php) that the ubuntu build and the upstream build both support version 1.8 of javascript.

---

### Post by n0manarmy on 2008-12-06
> **jamesstansell said:**
> Thanks.  Now I see what you mean.

Wow - I had a look at their code and it's pretty scary.  (Not the worse I've ever seen though.)

They're not checking javascript versions the recommended way.  Instead using some spaghetti logic based on browser name.

My first guess is that the difference in the user agent string is confusing their spaghetti.

You can tell from [http://browserspy.dk/javascript.php](http://browserspy.dk/javascript.php) that the ubuntu build and the upstream build both support version 1.8 of javascript.

When you say "their code" are you referring to webtycho or firefox? Ultimately I think this is something that should be fixable on my end since it acts differently between the two versions of firefox. I know I can use two browsers to access the system but when doing heavy research and classwork it just gets to be extremely tedious and I would prefer to keep it in one browser as much as possible.

---

### Post by nanotube on 2008-12-06
try copying the user agent string from the official mozilla build, and use 'user agent switcher' extension to set ubuntu build's user agent to that. see if that fixes things.

if things work with the new user agent, then you'll know that it's not a difference in any firefox build particulars, but a problem with the website's user agent parsing.

---

### Post by n0manarmy on 2008-12-06
> **nanotube said:**
> try copying the user agent string from the official mozilla build, and use 'user agent switcher' extension to set ubuntu build's user agent to that. see if that fixes things.

if things work with the new user agent, then you'll know that it's not a difference in any firefox build particulars, but a problem with the website's user agent parsing.

That worked. I grabbed the default settings from firefox that was directly downloaded from Mozilla's website and copied them over to a new profile in User Agent Switcher and I'm now able to use firefox that came with ubuntu in webtycho! Thank you very much!

This can be marked as resolved.

---

### Post by nanotube on 2008-12-07
> **n0manarmy said:**
> That worked. I grabbed the default settings from firefox that was directly downloaded from Mozilla's website and copied them over to a new profile in User Agent Switcher and I'm now able to use firefox that came with ubuntu in webtycho! Thank you very much!

This can be marked as resolved.

good! :)

since this proves that the fault was with their javascript version detector, i suggest you file a bug with that website to let them know. maybe pointing them to this thread would help... :)

---

### Post by jamesstansell on 2008-12-07
> **n0manarmy said:**
> When you say "their code" are you referring to webtycho or firefox? Ultimately I think this is something that should be fixable on my end since it acts differently between the two versions of firefox. I know I can use two browsers to access the system but when doing heavy research and classwork it just gets to be extremely tedious and I would prefer to keep it in one browser as much as possible.

I meant the webtycho javascript code.  (sorry I wasn't clearer.)  I'm glad nanotube understood what i meant and was able to offer a usable suggestion for you.

---

