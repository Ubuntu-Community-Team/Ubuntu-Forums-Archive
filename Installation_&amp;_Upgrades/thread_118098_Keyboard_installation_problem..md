---
title: "Keyboard installation problem."
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by jingo811 on 2006-01-16
Hi I just downloaded the Breezy .iso yesterday and burnt it to CD today.  And I was just about to install it from the Boot CD but stumbled on my first problem before I even got to install anything.

In the setup screen where you identify your keyboard language.  I chose SWEDEN, and then I tested it which proved to be wrong.
So I tried the most closest keyboard mapping I could think of which was American and British-English.  But no go there also.

So I tried to let the setup CD figure it out by itself letting me to punch in the specific **SWEDISH characters [å ä ö]** but I still got weird keyboard mapping.  It said that I had a Turkish keyboard :confused: This isn't the first time I install Linux, even though I'm still classed as Newbie, but I know where my keyboard come from 100%.

**How can I fix this installation problem?**  I didn't have this kind of trouble with Warty Warthog.

---

### Post by encompass on 2006-01-16
I probably have a close keyboard... try fi or finnish.  That may help.  Tell us if it works.

---

### Post by jingo811 on 2006-01-17
Oh I see what went whack with the installation!
I'm used to choose what language to use when installing various softwares to play with.  Usually I prefer having an **English speaking Interface** when messing with programs such as Gimp instead of using my **native Swedish interface**.

So during the setup I chose English as language, Sweden as location, that combination seemed to confuse Ubuntu: Breezy making it impossible to find the correct keymapping no matter what I did in the troubleshooting screen.

So choosing the setup in this order instead: Swedish - language, Sweden - location.  Made Breezy find the correct keymapping.  But now I don't have an English Interface anymore as in Hoary :-(  Swedish Interfaces makes things complicated the translation forces me to doublecheck translation every time somebody gives me Tutorial advises in english :-( :-(

---

### Post by encompass on 2006-01-23
Too the rescue.... you can have many languages at the same time... I do that with my wife... she is finnish and I am english...
> SYSTEM -> ADMINISTRATION -> LANGUAGE SELECTOR
If you don't have the language installed... it will install it for you.  That should help.

---

### Post by jingo811 on 2006-02-17
tnx will try that very soon :mrgreen:

---

### Post by gaiterin on 2008-05-10
Hi.
Maybe you must modify this:
System/Preferences/Keyboard -> Put in your language the layout.

or

System/preferences/SCIM Method Input -> Put in your language ;)

Regards.

---

