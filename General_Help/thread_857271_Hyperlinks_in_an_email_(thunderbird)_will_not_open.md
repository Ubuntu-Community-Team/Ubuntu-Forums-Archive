---
title: "Hyperlinks in an email (thunderbird) will not open a browser window"
date: 2008-07-12
forum: General Help
---

### Post by RembrandtQEinstein on 2008-07-12
I am running 
Thunderbird 2.0.0.14
Firefox 3.0
Ubuntu 8.04

I believe it was when I upgraded to Hardy that the browser will no longer open when I click on a hyperlink in a Thunderbird email.

I checked all the settings in TB, including the config editor. I read the sticky for Hardy known issues and I searched the knowledgebase. It is entirely possible I just overlooked the solution somewhere but never the less, I haven't found a solution.

Does any one know how to fix this or direct me to some way of debugging the problem myself?

Thanks

---

### Post by Elfy on 2008-07-12
Have you changed the preferred application e-mail to thunderbird from evolution - that's all I needed to do to get links to work

---

### Post by RembrandtQEinstein on 2008-07-12
First, thanks for the quick reply.
Second, I feel like an idiot.

I searched everywhere but the most obvious place. Both the email and browser preferred applications where set to custom. I set the browser to FF and email to TB and now I can open hyperlinks from email.

Thanks!

---

### Post by stalkingwolf on 2008-10-15
I have the same problem.  The preference settings are set to
firefox and thunderbird.

I am using UbuntuEEE 8.04.1 , Firefox2, and Thunderbird 2.0

---

### Post by Elfy on 2008-10-15
If you are using an old version of firefox - try to set it to custom and look for firefox 2 I would imagine that it expects firefox to in fact be ff3

I haven't got ff2 installed but would look in /usr/bin

---

### Post by Ms_Angel_D on 2008-10-15
The Thunderbird extension [thunderbrowse]("http://thunderbrowse.com/") can fix the issue as well you may wish to give it a try

---

### Post by stalkingwolf on 2008-10-15
I got this fixed by adding these 2 strings in the thunderbird config editor,

network.protocol-handler.app.http
network.protocol-handler.app.https

---

### Post by poliltimmy on 2008-12-07
> **stalkingwolf said:**
> I got this fixed by adding these 2 strings in the thunderbird config editor,

network.protocol-handler.app.http
network.protocol-handler.app.https

Done that no go

I have done every step mentioned still no luck. tbird will not launch firefox2. I have tried to completely remove and fresh installs. After an hour of uninstalling and trying each solution on a fresh install I must come to the conclusion that Ubuntu does not take this seriously. And neither does Mozilla.

Ubuntu 8.04.1 AMD 64
Firefox 2 (out of the repos)
Tbird (out of repos)

  Since all come from Ubuntu repros, why they will not work together baffles me. Could have removing Evolution from my system caused this?

---

### Post by poliltimmy on 2008-12-07
> **stalkingwolf said:**
> I got this fixed by adding these 2 strings in the thunderbird config editor,

network.protocol-handler.app.http
network.protocol-handler.app.https

Done that no go

I have done every step mentioned still no luck. tbird will not launch firefox2. I have tried to completely remove and fresh installs. After an hour of uninstalling and trying each solution on a fresh install. I have tried all launchpad solutionsI must come to the conclusion that Ubuntu does not take this seriously. And neither does Mozilla. 

Ubuntu 8.04.1 AMD 64
Firefox 2 (out of the repos)
Tbird (out of repos)

  Since all come from Ubuntu repros, why they will not work together baffles me. Could have removing Evolution and FF3 from my system caused this?

---

### Post by poliltimmy on 2008-12-07
sorry for the double post

---

### Post by poliltimmy on 2008-12-07
> **MetalHellsAngel said:**
> The Thunderbird extension [thunderbrowse]("http://thunderbrowse.com/") can fix the issue as well you may wish to give it a try

The Thuderbrowse extension will work, kind of. It's a bit awkward but the links will open inside Tbird . The right click: Visit in Browser does not work on my machine. The other options are working fine. And fast too. I guess I can live with it.

---

### Post by GrfyGrumpyBear on 2008-12-07
> **poliltimmy said:**
> The Thuderbrowse extension will work, kind of. It's a bit awkward but the links will open inside Tbird . The right click: Visit in Browser does not work on my machine. The other options are working fine. And fast too. I guess I can live with it.

In ThunderBrowse, the wizard asks you if you would like to fix link launching or use it as a browser.

Visit in Browser has two ways of working. The first works if you have defined a path to the browser.

However, if you don't want to define a path. Then make sure that you have a pref:

network.protocol-handler.external-default

and it's set to true.

ThunderBrowse (or BrowsrBounce [ThunderBrowse without the Browsing features]) will take it from there.

---

