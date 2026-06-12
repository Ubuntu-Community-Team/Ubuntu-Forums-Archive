---
title: "Hardy - Wrong version of Firefox"
date: 2008-09-18
forum: General Help
---

### Post by ngms27 on 2008-09-18
I've updated to Hardy from Dapper and still finding that Firefox 2.0.0.6 is loading despite everything saying Firefox 3 is installed.

Any ideas how to make Firefox 3 launch?

---

### Post by whizbaby on 2008-09-18
try from terminal
```
firefox-3.0
```
:)

---

### Post by ngms27 on 2008-09-18
Even that brings up Firefox version 2.0.0.6

---

### Post by LowSky on 2008-09-18
stay with 2.0.0.6, FF3 is crap IMHO

---

### Post by ngms27 on 2008-09-18
Well that's not the impression I get using it on my Windows box at work everyday!

---

### Post by LowSky on 2008-09-18
Windows and Linux versions of FF3 are very different, for some reason FF3 is alot better on Windows. The Linux version seems buggy to me.

---

### Post by lswest on 2008-09-18
can you post the output of ```
aptitude search firefox
``` from the terminal?

It will tell us if 3.0 is installed, and if it is, try removing the 2.0 install.

---

### Post by anotherdisciple on 2008-09-18
> **LowSky said:**
> Windows and Linux versions of FF3 are very different, for some reason FF3 is alot better on Windows. The Linux version seems buggy to me.

I disagree... It works awesome for me... much better.

---

### Post by ngms27 on 2008-09-18
root@ngms27-desktop:/home/ngms27# aptitude search firefox
i   firefox                         - meta package for the popular mozilla web b
p   firefox-2                       - lightweight web browser based on Mozilla  
p   firefox-2-dbg                   - debugging symbols for firefox-2           
p   firefox-2-dev                   - Development files for Mozilla Firefox     
p   firefox-2-dom-inspector         - tool for inspecting the DOM of pages in Mo
p   firefox-2-gnome-support         - Support for Gnome in Mozilla Firefox      
p   firefox-2-libthai               - Support for Thai line breaking in Firefox 
i A firefox-3.0                     - safe and easy web browser from Mozilla    
p   firefox-3.0-dev                 - Development files for Mozilla Firefox     
p   firefox-3.0-dom-inspector       - dummy upgrade package for firefox-3.0-dom-
i A firefox-3.0-gnome-support       - Support for Gnome in Mozilla Firefox      
p   firefox-3.0-venkman             - dummy upgrade package for firefox-3.0-venk
p   firefox-dev                     - meta package pointing to the latest develo
p   firefox-dom-inspector           - meta package for firefox-dom-inspector    
i   firefox-gnome-support           - meta package pointing to the latest gnome-
p   firefox-granparadiso            - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-dev        - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-dom-inspec - dummy upgrade package for firefox-granpara
p   firefox-granparadiso-gnome-supp - dummy upgrade package for firefox-granpara
p   firefox-greasemonkey            - firefox extension that enables customizati
p   firefox-launchpad-plugin        - Launchpad firefox integration             
p   firefox-libthai                 - dummy upgrade package for firefox-libthai 
p   firefox-sage                    - lightweight RSS and Atom feed reader for F
p   firefox-showcase                - Showcase provides a new way to manage your
p   firefox-themes-ubuntu           - Firefox themes matching the Ubuntu desktop
p   firefox-trunk                   - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-dev               - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-dom-inspector     - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-gnome-support     - dummy upgrade package for firefox-trunk ->
p   firefox-trunk-venkman           - dummy upgrade package for firefox-trunk ->
p   firefox-ubuntu-it-menu          - Firefox extension for a quick browse of Ub
p   firefox-webdeveloper            - web developer extension for the Firefox we
p   mozilla-firefox-adblock         - advertisement blocking extension for web b
p   mozilla-firefox-locale-af       - Mozilla Firefox Afrikaans language/region 
p   mozilla-firefox-locale-ar       - Mozilla Firefox Arabic language/region pac
p   mozilla-firefox-locale-be       - Mozilla Firefox Belarusian language/region
p   mozilla-firefox-locale-bg-bg    - Mozilla Firefox Bulgarian language/region 
p   mozilla-firefox-locale-bn-bd    - Transitional package for unavailable langu
p   mozilla-firefox-locale-bn-in    - Transitional package for unavailable langu
p   mozilla-firefox-locale-ca       - Mozilla Firefox Catalan; Valencian languag
p   mozilla-firefox-locale-cs-cz    - Mozilla Firefox Czech language/region pack
p   mozilla-firefox-locale-da-dk    - Mozilla Firefox Danish language/region pac
p   mozilla-firefox-locale-de-de    - Mozilla Firefox German language/region pac
p   mozilla-firefox-locale-el       - Mozilla Firefox Greek, Modern (1453-) lang
i   mozilla-firefox-locale-en-gb    - Mozilla Firefox English language/region pa
p   mozilla-firefox-locale-es-ar    - Mozilla Firefox Spanish; Castilian languag
p   mozilla-firefox-locale-es-es    - Mozilla Firefox Spanish; Castilian languag
p   mozilla-firefox-locale-eu       - Mozilla Firefox Basque language/region pac
p   mozilla-firefox-locale-fi-fi    - Mozilla Firefox Finnish language/region pa
p   mozilla-firefox-locale-fr-fr    - Mozilla Firefox French language/region pac
p   mozilla-firefox-locale-fy-nl    - Mozilla Firefox Western Frisian language/r
p   mozilla-firefox-locale-ga-ie    - Mozilla Firefox Irish language/region pack
p   mozilla-firefox-locale-gu-in    - Mozilla Firefox Gujarati language/region p
p   mozilla-firefox-locale-he-il    - Mozilla Firefox Hebrew language/region pac
p   mozilla-firefox-locale-hr       - Transitional package for unavailable langu
p   mozilla-firefox-locale-hu-hu    - Mozilla Firefox Hungarian language/region 
p   mozilla-firefox-locale-it-it    - Mozilla Firefox Italian language/region pa
p   mozilla-firefox-locale-ja-jp    - Mozilla Firefox Japanese language/region p
p   mozilla-firefox-locale-ka-ge    - Mozilla Firefox Georgian language/region p
p   mozilla-firefox-locale-ko       - Mozilla Firefox Korean language/region pac
p   mozilla-firefox-locale-ku       - Mozilla Firefox Kurdish language/region pa
p   mozilla-firefox-locale-lt       - Mozilla Firefox Lithuanian language/region
p   mozilla-firefox-locale-mk-mk    - Mozilla Firefox Macedonian language/region
p   mozilla-firefox-locale-mn       - Mozilla Firefox Mongolian language/region 
p   mozilla-firefox-locale-nb-no    - Mozilla Firefox Norwegian Bokm?l; Bokm?l, 
p   mozilla-firefox-locale-nl-nl    - Mozilla Firefox Dutch; Flemish language/re
p   mozilla-firefox-locale-nn-no    - Mozilla Firefox Norwegian Nynorsk; Nynorsk
p   mozilla-firefox-locale-nso      - Mozilla Firefox Northern Sotho language/re
p   mozilla-firefox-locale-pa-in    - Mozilla Firefox Panjabi; Punjabi language/
p   mozilla-firefox-locale-pl-pl    - Mozilla Firefox Polish language/region pac
p   mozilla-firefox-locale-pt-br    - Mozilla Firefox Portuguese language/region
p   mozilla-firefox-locale-pt-pt    - Mozilla Firefox Portuguese language/region
p   mozilla-firefox-locale-ro-ro    - Mozilla Firefox Romanian language/region p
p   mozilla-firefox-locale-ru-ru    - Mozilla Firefox Russian language/region pa
p   mozilla-firefox-locale-sk       - Mozilla Firefox Slovak language/region pac
p   mozilla-firefox-locale-sl-si    - Mozilla Firefox Slovenian language/region 
p   mozilla-firefox-locale-sv-se    - Mozilla Firefox Swedish language/region pa
p   mozilla-firefox-locale-tr-tr    - Mozilla Firefox Turkish language/region pa
p   mozilla-firefox-locale-zh-cn    - Mozilla Firefox Chinese language/region pa
p   mozilla-firefox-locale-zh-tw    - Mozilla Firefox Chinese language/region pa
p   mozilla-firefox-locale-zu       - Mozilla Firefox Zulu language/region packa
p   mozilla-firefox-webdeveloper    - web developer extension (transitional pack
v   totem-gstreamer-firefox-plugin  -                                           
v   totem-xine-firefox-plugin       -                                           
root@ngms27-desktop:/home/ngms27#

---

### Post by ThrobbingBrain66 on 2008-09-18
EDIT: Nevermind.  I hadn't read the last post before replying

---

### Post by whizbaby on 2008-09-18
> **ngms27 said:**
> Even that brings up Firefox version 2.0.0.6
o_O?
Ok, your list shows ff(s)3.0 is installed, so we will find and start it with brute force:
```
sudo updatedb
locate firefox|grep 3|grep bin
```
the output of the last command should give you the absolute path of the executable, lets say it says '/usr/bin/firefox-3.0'
then put exactly that into a terminal and hit return. If firefox2.0 is still showing up (bad bad dog, in the corner) give us the output of
```
ls -la /usr/bin/firefox-3.0
```
replacing /usr/bin/firefox-3.0 with the actual path you found.

---

### Post by ngms27 on 2008-09-19
Firefox 2.0.0.6 still launches.

ngms27@ngms27-desktop:~$ ls -la /usr/bin/firefox-3.0
lrwxrwxrwx 1 root root 31 2008-07-29 08:36 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.1/firefox.sh
ngms27@ngms27-desktop:~$

---

### Post by lswest on 2008-09-19
can you post the output of ```
ls ~/.mozilla/
```  if your profile for 2.0 is still there, try renaming it to something like firefox-2-bak and see if it then launches as 3.0.  Could be that the profiles are being mixed up and that it just appears to be 2.0.

---

### Post by whizbaby on 2008-09-19
Indeed, you have firefox-3.0 installed and 
/usr/bin/firefox-3.0
will fire it up for sure (no way its starting 2.0, I just took a look at /usr/lib/firefox-3.0/firefox.sh). All it can do is load your 2.0 profile or convert a beta profile, so please try what lswest suggests. That will force firefox to make a new config file(hopefully).

---

