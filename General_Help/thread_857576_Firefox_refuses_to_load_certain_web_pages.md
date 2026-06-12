---
title: "Firefox refuses to load certain web pages"
date: 2008-07-12
forum: General Help
---

### Post by vulcan707 on 2008-07-12
Hi there.

As from yesterday I am experiencing problems with Firefox 3.0. When I enter certain web pages, like the BBC's ([www.bbc.co.uk](www.bbc.co.uk)) Firefox will close completely, without any previous warning or error message.

Has anybody experienced similar problems, or know what might be wrong?

Thanks.

---

### Post by spiderbatdad on 2008-07-12
try launching firefox from a terminal to see if an error message is generated when you navigate to that site.```
firefox
```

---

### Post by vulcan707 on 2008-07-12
When launched from a terminal this is what I get when I try to access the BBC's page:


** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return
Segmentation fault

---

### Post by spiderbatdad on 2008-07-12
seg fault can be caused by many things...hard to pin down. could be heat...hardware...memory...maybe you have the infamous default folder in your home ./firefox directory...or ./mozilla/firefox directory...whatever. there are threads concerning an enormous folder that gets written into the hidden directory url<something or other> default....

I don't use firefox personally. I prefer seamonkey. You can install it by installing the iceape packages in synaptic package manager.

---

### Post by vulcan707 on 2008-07-12
> **spiderbatdad said:**
> seg fault can be caused by many things...hard to pin down. could be heat...hardware...memory...maybe you have the infamous default folder in your home ./firefox directory...or ./mozilla/firefox directory...whatever. there are threads concerning an enormous folder that gets written into the hidden directory url<something or other> default....

I don't use firefox personally. I prefer seamonkey. You can install it by installing the iceape packages in synaptic package manager.

I don't think the problem is caused by heat, hardware or memory, because it just seems to happen with certain web pages, like the one I mentioned. I don't have any problems opening others. It was all working well up to yesterday.

I'll try to find the threads you mentioned.

---

### Post by spiderbatdad on 2008-07-12
somewhere in the archives...there are tons of threads regarding firefox problems

the file is ./mozilla/firefox/something.default/urlclassifier3.sqlite hidden in your home directory.

you can safely delete the urlclassifier3.sqlite and restart firefox

---

### Post by vulcan707 on 2008-07-12
> **spiderbatdad said:**
> somewhere in the archives...there are tons of threads regarding firefox problems

the file is ./mozilla/firefox/something.default/urlclassifier3.sqlite hidden in your home directory.

you can safely delete the urlclassifier3.sqlite and restart firefox

No luck. I deleted urlclassifier3.sqlite and the problem is still there. Maybe I should just remove firefox completely and try installing it again.

---

### Post by spiderbatdad on 2008-07-12
it looks like a problem with one of your firefox plugins when accessing that page. I would try disabling the plugins and reenabling them one at a time...try  the page each time, to see which one is offending.

---

### Post by vulcan707 on 2008-07-12
> **spiderbatdad said:**
> it looks like a problem with one of your firefox plugins when accessing that page. I would try disabling the plugins and reenabling them one at a time...try  the page each time, to see which one is offending.

Bullseye!

I looked up in the synaptic package manager history for any recent plugins intalled. I found this one:

Upgraded the following packages:
flashplugin-nonfree (9.0.124.0ubuntu2) to 10.0.1.218+10.0.0.525ubuntu1~hardy1

I disabled in Firefox the plugin "Shockwave Flash 10.0.0d525".

Now the web pages I had trouble with load without problems.

Many thanks for your patience and guidance spiderbatdad!

---

### Post by Master Chief on 2008-07-12
> **vulcan707 said:**
> When launched from a terminal this is what I get when I try to access the BBC's page:


** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f138: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return
GCJ PLUGIN: thread 0x805f138: NP_GetValue
GCJ PLUGIN: thread 0x805f138: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f138: NP_GetValue return
Segmentation fault

This GCJ PLUGIN error is coming from a plugin called "gcjwebplugin" aka IcedTea.  Let's see, does the following website work for you:

[http://javatester.org/version.html](http://javatester.org/version.html)

---

### Post by Master Chief on 2008-07-12
> **vulcan707 said:**
> ....I disabled in Firefox the plugin "Shockwave Flash 10.0.0d525".

Now the web pages I had trouble with load without problems....

So you fixed a failing plug-in aka gcjwebplugin by disabling flash?

---

### Post by vulcan707 on 2008-07-12
> **Master Chief said:**
> This GCJ PLUGIN error is coming from a plugin called "gcjwebplugin" aka IcedTea.  Let's see, does the following website work for you:

[http://javatester.org/version.html](http://javatester.org/version.html)

Hi Master Chief.

The problem seemed to be caused by the plugin "Shockwave Flash 10.0.0d525". At least when I disable it the pages will load.

The page javatester.org, works for me even when the shockwave plugin is enabled.

---

