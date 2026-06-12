---
title: "ATI HD5145 kills install on Toshiba L650-10G"
date: 2010-08-17
forum: Hardware
---

### Post by clarkac on 2010-08-17
I installed Lucid on my new Toshiba L650-10G with an ATI HD 5145 graphics card.  After a reboot the screen is blank, although it's obvious that the system is up & running.  I have gone through the two possibilities of graphics driver - tried the builtin driver (which fails to install) and a native linux driver downloaded from ATI (which does install) and also tried not installing either.  

I'm stuck.  Any suggestions before I abandon Ubuntu?

Andy

---

### Post by clarkac on 2010-08-19
I have managed to get round this problem. Firstly, by installing the ATI native driver, then by not installing fglrx-modaliases in the Update Manager and by unchecking 'Prorietary drivers for devices' in the settings for Update Manager. So far, so good.  One or two other problems, but this problem has been overcome.;)

---

### Post by nilsja on 2010-09-17
is it now runing stable? did you make any other modifications?

i cant even get the live-cd running stable here...

---

### Post by clarkac on 2010-09-17
Yes, running OK.  I had to install the native Linux drivers for the wireless hardware and that is Ok too.  No real problems so far after the initial hiccup.

---

### Post by nilsja on 2010-09-17
ok cool. what do you mean by "native Linux drivers"? How to install them? And could you just install it without any acpi=off kernel options?

i have a L650d-11G here.

---

### Post by clarkac on 2010-09-17
Take a look at this thread which guides you to the manufacturer's driver page [http://ubuntuforums.org/showthread.php?t=1425140](http://ubuntuforums.org/showthread.php?t=1425140)
I simply downloaded & installed after which wireless works well.

---

