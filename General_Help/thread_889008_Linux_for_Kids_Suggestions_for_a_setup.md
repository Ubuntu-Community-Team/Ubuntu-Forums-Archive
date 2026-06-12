---
title: "Linux for Kids: Suggestions for a setup?"
date: 2008-08-13
forum: General Help
---

### Post by ATSC on 2008-08-13
My little cousin has just come into class 5 and should get a pc now. I want to give her edubuntu. The family is used to use winblow$ though and therefore it should be set up for easy maintenance. Being a Ubuntu noob myself I'd appreciate some recommendations regarding the settings, the set up and/or other changes that you'd suggest. I've already deleted OO, Gimp and other stuff that I find useless for kids in this age.

---

### Post by phidia on 2008-08-13
Just a thought but it might be nice to set up AWN ([Avante WIndow Navigator]("http://wiki.awn-project.org/index.php?title=Main_Page")) as an easy to access program launcher.

---

### Post by mb_webguy on 2008-08-13
Edubuntu is fairly child friendly as it is, and Ubuntu distributions are fairly easy to maintain once after the initial setup.  I'd suggest making one user account for the child and one for adults and administration purposes.  You should probably remove the child account from the admin group so they can't accidentally do any serious damage to the system.

I'm not sure I would have deleted OOo or Gimp...  There's no harm in letting the kids get accustomed to applications that they'll eventually need to use later on.  Besides, while the computer may be for a child, the time may come when an adult may need to use it (such as if the parents' computer crashes).  If you really don't think the child should have access to these programs yet, you could simply uncheck the entry in the Gnome menu.  That way the programs are still there (without having to reinstall them) if you need them, yet the child doesn't have easy access.  Likewise, for a very young child I think I'd edit the Gnome menu to remove the Preferences and Administration submenus.  There's really not anything in those menus that a young child should need to access.

The main issue people tend to have setting up child-friendly system is Internet access.  Fortunately, the extensible and customizable nature of Firefox makes this moderately easy.  The [ProCon Latte]("https://addons.mozilla.org/en-US/firefox/addon/1803") extension will let you blacklist (or whitelist) websites, to prevent the impressionable kiddies from stumbling across naughty websites.  Since the kids could disable ProCon Latte using the AddOns menu, you can remove that menu (and any others you don't think they should access) using the [Menu Editor]("https://addons.mozilla.org/en-US/firefox/addon/710") extension.  A few other extensions that might be nice for a child would be [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") (though ProCon Latte may possibly stop adds anyway), [Googlepedia]("https://addons.mozilla.org/en-US/firefox/addon/2517") (for curious minds), [URL Fixer]("https://addons.mozilla.org/en-US/firefox/addon/2871") (since little fingers don't always hit the right keys), and [NoSquint]("https://addons.mozilla.org/en-US/firefox/addon/2592") (if you have a high-resolution moniter, to make words easier to read and links easier to click).

I also agreee with phidia's suggestion of the Avant Window Navigator ("sudo apt-get install avant-window-navigator").

---

### Post by Howitzer777 on 2008-08-13
I would seriously recommend the glubble extension for firefox. [http://lifehacker.com/software/featured-firefox-extension/approve-sites-your-kid-visits-with-glubble-270139.php](http://lifehacker.com/software/featured-firefox-extension/approve-sites-your-kid-visits-with-glubble-270139.php)



internet should be the only thing you have to be worried about with edubuntu. 

becareful if you want her to have pidgin, or any im service installed. some people freak out about that.

---

### Post by mb_webguy on 2008-08-13
YMMV, but I don't like the Glubble extension because it *completely* changes how you browse the Web.  It is a drastic departure from the usual browsing experience.  While it does a very good job at what it is intended to do, I personally don't like the way it does so.

The method I described above using ProCon Latte provides the same degree of kid-safe browsing without dramatically altering the way you use the browser.

But it's basically just personal preference...

---

