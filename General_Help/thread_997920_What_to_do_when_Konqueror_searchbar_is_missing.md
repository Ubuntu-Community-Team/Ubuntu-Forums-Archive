---
title: "What to do when Konqueror searchbar is missing"
date: 2008-11-30
forum: General Help
---

### Post by optikos on 2008-11-30
Because replies to threads before 21apr2008 are inhibited, this is a more complete answer than what was provided in that now-read-only thread [http://ubuntuforums.org/showthread.php?t=701716](http://ubuntuforums.org/showthread.php?t=701716)

[FONT="Times New Roman"]**Preexisting original post:  From Freddy **
***Konqueror Search Bar?*** 
Greetings all.
    I use a kde-core setup of KDE and thought that this time I should use Konqueror for web browsing but I'm having some trouble with making 'Google Search Bar' to appear.
    I searched around for a while and saw a bunch of tip about going into 'settings | configure toolbars' and to choose 'Searchbar <serachbar> from there but it doesn't appear for me using that way. I have already checked 'google searchbar' inside 'configure extensions'
    Are there any frindly souls out there with some idea of what to do?
    Thanks.

**Preexisting eply by p_quarles:**
***Re: Konqueror Search Bar?*** 
I don't believe there is a separate search bar for Konqueror (at least not that I can find), but you can do this:
 1) Go to Settings >> Configure Konqueror >> Web Shortcuts
 2) Change the "Default Search Engine" from "None" to "Google."
 3) You can now enter search terms into the location bar and it will return results from Google.

**Preexisting reply by Whiffle:**
***Re: Konqueror Search Bar?*** 
There is, but I never use it. I just type:
 gg: search terms here 
  in the address bar, and it does google. You can add your own too under what p_quarles said. Its quite powerful.

**Preexisting reply by oobuntoo:**
***Re: Konqueror Search Bar?*** 
It's easy to get konqueror search toolbar back.
 click on:
 Settings -> Configure Toolbars..
 On the drop-down menu, choose "Search Toolbar"
  move "Search Bar" on the left window/box to the right window/box and click apply. You may have restart konqueror to see the search toolbar.

**Preexisting reply by Mazetas:**
***Re: Konqueror Search Bar?*** 
there is no search toolbar in these options. the first solution, transforming location bar to google bar, isn't enough satisfying.
 so any other suggestion on how to appear google search bar in Konqueror?
[/FONT]
**New reply by optikos:**
     The replies by p_quarles, Whiffle, and oobunutoo are all _good training_ for **when the konq-plugin searchbar is *already installed***.  But what all 3 of those replies did not diagnose was the situation that I (and apparently Freddy and Mazetas too) have:  We do not have konq-plugin searchbar installed at all.  Thus there was none of the configuration parameters that p_quarles and oobuntoo train us to tune.  I had the searchbar plugin installed until I accidentally deinstalled all of KDE4.1 in adept.
      (When trying to deinstall a piece of base-KDE that I will never execute, [nearly?] all of KDE was deinstalled including all of Konqueror and all of its plug-ins---oops, I did not request that *overreaching extrapolation*!  So I reinstalled KDE4.1, Konqueror, and numerous other K-prefixed packages.  The trouble is inventorying all of the pieceparts to reinstall.  Perhaps Freddy and Mazetas had some similar accident where adept(1)ly trying to delete a piece of something that appears to be separately installable/deinstallable, instead deleted all of western civilization.)
     Instead, the solution to this root-cause problem of entirely missing the searchbar plugin is to reinstall whichever of the canonical konq-plugins are missing for whatever reason:
[FONT="Courier New"]sudo apt-get install konq-plugins[/FONT]

---

