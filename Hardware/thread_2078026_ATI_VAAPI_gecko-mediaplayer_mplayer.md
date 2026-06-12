---
title: "ATI VAAPI gecko-mediaplayer mplayer"
date: 2012-10-29
forum: Hardware
---

### Post by vanquishedangel on 2012-10-29
Hi I have a few issues to resolve and the first one is I have an ati radeon hd 6450 in an hp 5750. I want to know if a form of va-api is implemented and working in lubuntu, I use the proprietary drivers from jockey. I really just want the graphics card to do more of the work for videos and such rather than the processor. Usage is quite low in mplayer so this isnt really that important.

Issue 2 however is that I use chromium as my main browser and I would like to use mplayer (gecko-mediaplayer) to play flash on as many sites as possible. I tested this in firefox (16.0.2)and it works in that browser but in chromium(22.0.1229.94) it does not

I use a greasemonkey script ([http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)) that replaces the flash player with mplayer using the gecko-mediaplayer plugin.

I ran chromium from the terminal and got this
Moonlight: 3.99.0.3
Moonlight: Attempting to load libmoonloaderxpi 
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[44:44:2054147634:ERROR:webplugin_delegate_proxy.cc(379)] PluginMsg_Init returned false
[44:44:2054147736:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in

That is weird because I don't have a nvidia graphics card and why is moonlight loading?

When i disabled moonlight and tried in terminal again I get this

Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[44:44:2436760492:ERROR:webplugin_delegate_proxy.cc(379)] PluginMsg_Init returned false
[44:44:2436760692:ERROR:webplugin_impl.cc(269)] Couldn't initialize plug-in


a yellow bar pops up in chromium and says "could not load mplayer-plugin is now gecko-mediaplayer 1.0.6." The video tested is here [http://www.youtube.com/watch?v=dsDTJ__jioo&feature=related](http://www.youtube.com/watch?v=dsDTJ__jioo&feature=related), it only runs when I tell it to use html5. But when mpeg or mpeg4 is selected (or auto) it gives the yellow bar. I suspect html5 works because the browser has its own player for that?

UPDATE: I got it working after much searching and trial and error.

I had to regress both gnome-mplayer and gecko-mediaplayer. I use Lubuntu 12.10 and I like to stick with just vanilla software from the repo. I uninstalled gnome-mplayer and Gecko-mediaplayer from synaptic (this will uninstall lubuntu-desktop) and completely remove them, I also used bleachbit afterwards. then I installed gnome-mplayer1.0.5-1 from the 12.04 repos, and installed gecko-mediaplayer 1.0.4-2 from the 12.04 repos as well. Then reinstall lubuntu-desktop from synaptic, while in synaptic highlight gnome-mplayer and gecko-mediaplayer click package>force version and choose the debs you just installed. :) This is a temporary fix that will hold you over until mplayer peeps fix the issue, it seems to be a regression. I will mark this thread as solved but will check it frequently to see if another answer comes along.

---

### Post by vanquishedangel on 2012-11-15
You can also choose lock version in synaptic as well, it seems to work better than force version.

I made the suggestion on Ubuntu Brainstorm to make a plugin or adaption to gecko-mediaplayer for flash, or that gnash should be a possible plugin, or lightspark that installs to the browser and uses mplayer, vlc, or totem etc, I see no need for 30 different players to be made when the ones that exsist already can play them, but that may not handle games. I also got hulu working in mplayer to.

But this Idea was marked as not being an Idea, I really hate when they do that lolz.

---

