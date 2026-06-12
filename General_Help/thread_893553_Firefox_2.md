---
title: "Firefox 2"
date: 2008-08-18
forum: General Help
---

### Post by FLCL on 2008-08-18
So whats with FF2 and not being able to install add-ons? 
I ditched FF3 because it's laggy and freezes up a lot on me, whereas FF2 runs fine...with the exception of not being able to install add-ons. 
Anyone know why? or can help?:confused:

---

### Post by Too Late on 2008-08-18
How is it unable to install? Error messages?

However, every site that wants to install add-ons, must have their permissions to do so. Go to Edit -> Preferences -> Security and check whether the sites are listed in the "Exceptions..." or not.

---

### Post by FLCL on 2008-08-18
It's the fact that i get an error. As follows:
[IMG]http://imagedash.com/images/bfi1219078148a.png[/IMG]

---

### Post by FLCL on 2008-08-18
bump

---

### Post by robotman5 on 2008-08-18
Hmmm when i had Linux and Firefox 2 i could add addons no problems at all !



(Themes)

have you tryed uninstall Firefox then reinstalling it?:confused:

---

### Post by FLCL on 2008-08-18
Yeah, many times =(

Im thinking it has something to do with it not being the default installation. It came with FF3, but i uninstalled it for FF2. I dont see why that would make any difference though

---

### Post by silkstone on 2008-08-18
You may have to uninstall the config files as well as the program. Go to ~/.mozilla/firefox and there should be a folder called xxx.default and a file called profiles.ini. You need to remove those to do a complete uninstall.

Now, I believe that FF2 may have a separate folder called firefox-2 or similar, also in ~/.mozilla

It could be that these have become confused, so to start again I would get rid of the lot.

---

### Post by fooman on 2008-08-18
no need to uninstall firefox 2 or delete the profile.  you just need to delete the *extensions.rdf* file which is found here:

~/.mozilla/firefox/*******.default (where ******* is a random set of numbers and letters)

delete the file, restart firefox and you should be good to go.

---

### Post by FLCL on 2008-08-18
Alright, i will try what you said fooman.

Edit: Woot, it works now :D. Thank you very much

---

