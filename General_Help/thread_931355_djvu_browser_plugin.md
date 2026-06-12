---
title: "djvu browser plugin"
date: 2008-09-27
forum: General Help
---

### Post by howlingmadhowie on 2008-09-27
hi everybody. i'm having difficulty getting the djvulibre browser plugin working. i've installed the package through synaptic and have gone to a page which delivers djvu files (for example: [http://djvu.org/gallery/documents/magazines/frameset.php?item=archaeology/index.djvu&param=zoom=50%20scrollbars=no%20navpane=thumbnails%20logo=yes%20layout=double%2Ccover%2Cnogap%20cache=yes%20toolbar=bottom,fixed-ruler%2Ccalibrate%2Cbackforw%2Clizard%2Cfore%2Cback%2Ccolor%2Cbw](http://djvu.org/gallery/documents/magazines/frameset.php?item=archaeology/index.djvu&param=zoom=50%20scrollbars=no%20navpane=thumbnails%20logo=yes%20layout=double%2Ccover%2Cnogap%20cache=yes%20toolbar=bottom,fixed-ruler%2Ccalibrate%2Cbackforw%2Clizard%2Cfore%2Cback%2Ccolor%2Cbw)), however the plugin doesn't start. looking in firefox an about:plugins reveals that no plugin has been installed. i've tried symbollically linking to the nsdjvu.so plugin (which was installed into /usr/lib/netscape/plugins-libc6) from all the /usr/lib/*/plugins/. places i could think of (netscape, firefox, mozilla, mozilla-firefox etc.) but the plugin is still not being found by firefox.

has anybody have the plugin working on ubuntu? i'm running a 64 bit version of 8.04 btw.

---

### Post by gerry0 on 2008-10-20
> **howlingmadhowie said:**
> 

has anybody have the plugin working on ubuntu? i'm running a 64 bit version of 8.04 btw.

I'm running 8.04 32 bit & have just gotten the djvu browser working.

Here's what I did.

Install the djvulibre plugin using synaptic (same as you)

cd /usr/lib/firefox-addons/plugins

sudo ln -s /usr/lib/mozilla-firefox/plugins/nsdejavu.so

Seems to work fine, plugin shows up in Firefox's plugins list.

---

### Post by howlingmadhowie on 2008-12-07
many thanks, that was the problem :)

---

### Post by ernst on 2009-05-23
> **gerry0 said:**
> I'm running 8.04 32 bit & have just gotten the djvu browser working.

Here's what I did.

Install the djvulibre plugin using synaptic (same as you)

cd /usr/lib/firefox-addons/plugins

sudo ln -s /usr/lib/mozilla-firefox/plugins/nsdejavu.so

Seems to work fine, plugin shows up in Firefox's plugins list.

Great! This was the solution for me too, but a succeeding error has popped up:

I can load and display any djvu image I've used to test djvu, but an ancestry archive site, that displays historical pages that were scanned for djvu display, does not display.  I had to load the firefox djvu plugin as this site demanded the ability to display djvu files.  Any idea what the reason(s) could be that a site cannot have its djvu images displayed while other sites can?  

Note: This site originally asked to have a djvu plugin loaded to see an image.  When I got djvu to work, this message no longer appeared - I even get an image id number, but no image.

Ernst

---

### Post by MarjaE on 2012-01-31
Um, can you explain the fix? Because I see there are a lot of djvulibre items, I'm not sure which ones to install, and the plugin finder crashed.

*Sigh*

I just want to read one book from the web archive, but the pdf is more than 100 megs more than the djvu. If the web archive would still just let users download the djvu, this wouldn't be an issue.

---

