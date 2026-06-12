---
title: "BBC Website takes ages to load in FF3."
date: 2008-08-07
forum: General Help
---

### Post by MedellinManDem on 2008-08-07
Does anyone know why this might be? 

EVERYtime I try and load it it takes an age. It's all of their news sites BBC News and BBC Sport.

---

### Post by dcstar on 2008-08-08
> **MedellinManDem said:**
> Does anyone know why this might be? 

EVERYtime I try and load it it takes an age. It's all of their news sites BBC News and BBC Sport.

Load what? - you have given no URL examples for people to test for themselves.

---

### Post by MedellinManDem on 2008-08-08
[http://news.bbc.co.uk/](http://news.bbc.co.uk/)

[http://www.bbc.co.uk/sport/](http://www.bbc.co.uk/sport/)

---

### Post by Elfy on 2008-08-08
Personally I found that ff3 was slow all the time. The site you give and all the rest load fine here - open a terminal and run

```
ip a | grep inet6
```

If you get an output you could try to disable ipv6, if there is no output it is disabled.

---

### Post by MedellinManDem on 2008-08-08
> **forestpixie said:**
> Personally I found that ff3 was slow all the time. The site you give and all the rest load fine here - open a terminal and run

```
ip a | grep inet6
```

If you get an output you could try to disable ipv6, if there is no output it is disabled.

```
 inet6 ::1/128 scope host 
    inet6 fe80::21c:23ff:fe89:d63f/64 scope link 


```

I got that output. How do I disable ipv6 and what is ipv6?

---

### Post by peakshysteria on 2008-08-08
Loads very well here.

My Firefox Information

Last updated: Fri, 08 Aug 2008 08:19:49 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

**Extensions** (enabled: 18, disabled: 1; total: 19)
[list]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.rjonna.com/ext/dictionarytip.php) 1.3 
[*][DownloadHelper](http://www.downloadhelper.net) 3.2 
[*][FireFTP](http://fireftp.mozdev.org) 1.0.1 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 [disabled]
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.7.7 
[*][Full Fullscreen](http://emsearcy.org) 3.1 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20080609.0 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7a 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål ordliste]() 2.0.10.0 
[*][Norsk Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.6.1.080416 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (5)
[list]
[*]Camifox 
[*]Default [selected]
[*]iFox 
[*]iFox Metal 
[*]PitchDark 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]GCJ Web Browser Plugin (using IcedTea) 1.0
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

**MedellinManDem**, what is your setup. Ubuntu? Which Firefox? Which addons are you running? Etc.... the more info we get the faster we can help you.

**forestpixie**, why disable ipv6? And what is your setup? Seems strange FF should be slow all the time since it really is known to be at least the second fastest browser out there.

---

### Post by Elfy on 2008-08-08
> How do I disable ipv6 and what is ipv6?I edit this file  /etc/modprobe.d/aliases to get rid

```
sudo cp  /etc/modprobe.d/aliases  /etc/modprobe.d/aliases.0808
gksudo gedit  /etc/modprobe.d/aliases
```
You don't tell which variant you use - above gksudo command good for ubuntu - kdesu kate for kubuntu or gksudo mousepad for xubuntu.

Near the top is line which looks like

> alias net-pf-10 ivp6change to 
> alias net-pf-10 offsave , close and reboot

These thread - goes through change and what ipv6 is 
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)
[https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)

---

### Post by fragos on 2008-08-08
> **MedellinManDem said:**
> [http://news.bbc.co.uk/](http://news.bbc.co.uk/)

[http://www.bbc.co.uk/sport/](http://www.bbc.co.uk/sport/)

The BBC sites are slower to load than other sites because of how they are coded. They are slow even on a fast cable connection and that startup would be greatly drawn out on slower connections. They need help -- this isn't a FF3 problem.

---

