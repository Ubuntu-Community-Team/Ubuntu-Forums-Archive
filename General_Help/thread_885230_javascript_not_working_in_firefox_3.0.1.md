---
title: "javascript not working in firefox 3.0.1"
date: 2008-08-09
forum: General Help
---

### Post by CurlersRock on 2008-08-09
I'm not sure when javascript stopped working, it was a few weeks, and quite a few updates ago.

I am running FF3.0.1 and Hardy Heron.  I downloaded Opera 9.5 and javascript works fine.

Javascript is enabled. At least under Preferences>Content Enable Javascript is checked. (Ditto Enable Java)

Checking the Error Console reveals:
Error: pop is not defined
Source File: javascript:pop('http://sat.wrh.noaa.gov/satellite/showsat.php?wfo=psr&area=west&type=vis&size=1');
Line: 1

But this happens on all sites with a javascript.

Cheers,
Dan

---

### Post by p_quarles on 2008-08-09
Javascript doesn't work at all? That seems like a pretty broad claim. Heck, this very forum uses Javascript pretty extensively for basic functionality. Perhaps you could be more specific about what isn't working, and where?

---

### Post by CurlersRock on 2008-08-10
thanks and sorry.  What I mean is whenever clik on a link that starts "javascript:" nothing happens.  If I click using the middle button, a new empty tab appears.

If I copy the text within the single quotes of, for example: "javascript:pop('http://sat.wrh.noaa.gov/satellite/showsat.php?wfo=psr&area=west&type=vis&size=1');" 
and paste into the address bar, the page will appear.

---

### Post by p_quarles on 2008-08-10
Okay. That sounds like a URI handling problem rather than a javascript problem. Can you confirm that other javascript-related things work okay? E.g., the "quick reply" button on the bottom of each post in this forum?

Also, can you test if these links that are broken in Ff 3.0.1 work in other browsers?

---

### Post by CurlersRock on 2008-08-10
> **p_quarles said:**
> Okay. That sounds like a URI handling problem rather than a javascript problem. Can you confirm that other javascript-related things work okay? E.g., the "quick reply" button on the bottom of each post in this forum?

Also, can you test if these links that are broken in Ff 3.0.1 work in other browsers?
If you mean the little the icon with 3 segment arrow, it does NOT work in FF.  
In Opera, the quick reply button does not even appear.  However the link that i described in my previous post DOES work in Opera.

Thanks.
Dan

---

### Post by CurlersRock on 2008-08-10
Oh.  my mistake.  I was expecting something else to happen with the quick reply button.  It DOES work in FF.

---

### Post by CurlersRock on 2008-08-11
> **CurlersRock said:**
> Oh.  my mistake.  I was expecting something else to happen with the quick reply button.  It DOES work in FF.

When I said "It DOES Work in FF" i meant the quick reply button.  I still have the trouble originally described.

...Dan

---

### Post by CurlersRock on 2008-08-17
Maybe I confused you.  The quick reply works in FF, I'm using it now.  I still have problems with the link "javascrit:pop('http://sat.wrh.noaa.gov/satellite/showsat.php?wfo=psr&area=west&type=vis&size=1');" in FF, but I do not have a problem with Opera.

---

### Post by Mickey1 on 2009-01-11
I am experiencing the same problem

I can for example play a game on yahoo without problems 
But trying to open a lounge on pogo with a javascript link seems impossible
Most links starting with javascript will not work 
For example:
Goto: pogo.com and select the game pop-it... this will all go well 
but to enter a gameroom i'd have to click s link similar to this:

[javascript:rc('poppit2-plpo2sf207');

which does not work.. it'll just display the link and nothing will happen

I've tried alot of different things but none seem to work 

I have added sites to allow pop-ups
I have enabled Java + Javascript

In about:plugins i get this on the Java
Java(TM) Plug-in 1.6.0_10-b33
All options below it are marked yes

At one point i thought i installed the latest update available from the site being java 6 update 11 but it is not showing up?

All this is happening with the canonical 1.0 release for firefox
It also does not work in Konqueror (not tried any other browser)

Hoping to get this resolved and thanks in advance for any help provided

Cheers

---

### Post by proofsetstar on 2009-05-06
i am having the same problem i have some sites that use java, but its not opening them i went to see the plug ins that are installed in firefox and java is not there but it's installed in the system running ubuntu 9.04.

---

### Post by lonelydragon757 on 2011-02-25
I am having a similar situation with Javascript...  it appears enabled in Firefox 3.6.15pre and 4.0b12pre.  but JavaScript used to work... no settings were changed by me (except maybe updating an addon here or there).   but an example, especially the 3.6.15. is google maps...  I attempt to click on Street View from an address. but NOTHING happens.  no error. no nothing...  but if I run chrome. it works fine...   there are other sites... that loads javascript automatically.  and changes the front page... but it keeps saying LOADING, may take 30 seconds. but never updates...   and top right corner of that page, it says loading javascript...

---

