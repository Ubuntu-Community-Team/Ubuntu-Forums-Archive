---
title: "Issue with  GNUcash Getting Quotes"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by mcglnx on 2009-06-03
Dear All,

Post installation of 9.04, I have some issues getting quotes in Gnucash.

I have the following message:
```

Unable to retrieve quotes for these items:
  CURRENCY:USD
Continue using only the good quotes?

```

Stdout gives the following:
```
Unable to retrieve quotes for these items:
  CURRENCY:USD
Continue using only the good quotes?
```

And on the logs, I have:
```
more /tmp/gnucash.trace 
* 22:59:59  CRIT <gnc.backend.file> commodity_ref_to_dom_tree: assertion `c' fai
led
* 23:00:00  CRIT <gnc.backend.file> commodity_ref_to_dom_tree: assertion `c' fai
led

```

Note I've ran ```
sudo gnc-fq-update
``` without any positive effect.

Does anyone has seen the same issue? 
Any clue on how to fix this? or plan to fix it?

Thanks in advance, 
D.

---

### Post by mcglnx on 2009-06-04
No idea?

---

### Post by ltdunbar on 2009-06-04
Hi,

I have had the same problem since updating to jaunty (9.04).

Micha&#322;

---

### Post by mcglnx on 2009-06-05
Ok at least it is reproducible.

---

### Post by mcglnx on 2009-06-06
Here I got a way to reproduce:

[LIST]
[*] Create New file
[*] Select Money: CHF
[*] Go to Tools->Price Editor
[*] Select "Show national currencies"
[*] Select "USD" currency.
[*] Now: Tools-> Price Editor
[*] "Get Quotes"
[*] Then you got the Following error:
```
Unable to retrieve quotes for these items:
  CURRENCY:USD
```
[/LIST]

On CLI, there nis not much information:
```

gnucash --debug --extra --add-price-quotes=test2
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.16
gwenhywfar-INFO: plugin.c:  577: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  577: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  577: Plugin type "dbio" unregistered

```

Note, I'm not sure if related, but finance::Quote looks to have some issue:
```
 /usr/share/doc/libfinance-quote-perl/examples/currency-lookup.pl USD CHF
Urgh!  Nothing back

```

Now we have a method to reproduce, we need to find how to fix. Any one has any hint?




Cheers.
D.

---

### Post by mcglnx on 2009-06-06
Additional reference: [http://sourceforge.net/mailarchive/message.php?msg_id=1985.456T2537T474706AmigaPhil%40scarlet.be](http://sourceforge.net/mailarchive/message.php?msg_id=1985.456T2537T474706AmigaPhil%40scarlet.be)

---

### Post by bupe on 2009-08-02
Dear all,

I have the same issue. Tried upgrading the perl files but I've never done this before and I'm not able to solve this by myself...

Is there any easy way to fix this? Google only turned up this forum... a howto or a step-by-step guide would be much appreciated!

Best regards,
Peter

---

### Post by bupe on 2009-08-06
I managed to fix this by installing F::Q from the git repo:
[http://github.com/pfenwick/finance-quote/tree/master](http://github.com/pfenwick/finance-quote/tree/master)

Using this guide:
[http://www.cpan.org/modules/INSTALL.html](http://www.cpan.org/modules/INSTALL.html)

Cheers,
Peter

---

### Post by mcglnx on 2009-08-20
Thanks. How to push this fix to mainstream? Shall we contact the maintainer?

---

### Post by zoubidoo on 2009-11-06
```
sudo gnc-fq-update
```
Solved it for me.

It downloaded and installed a bunch of perl modules.  Gnucash didn't even need restarting.

---

### Post by mcglnx on 2009-11-07
Well, it look it has been fixed with 9.10!!! That's great!

---

