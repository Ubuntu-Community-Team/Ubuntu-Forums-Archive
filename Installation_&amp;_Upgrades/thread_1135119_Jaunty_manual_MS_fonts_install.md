---
title: "Jaunty manual MS fonts install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ivanhelguera on 2009-04-24
EDIT 
I put it here by misteke - I copied it to General Help. 
[http://ubuntuforums.org/showthread.php?p=7133209#post7133209]("http://ubuntuforums.org/showthread.php?p=7133209#post7133209")
Is there any way to delete this one?

I was trying to install MS fonts manually (no, MSTTcorefonts is not enough). 
I created /usr/share/fonts/MS, and copied the ttfs from my ipod. (which came from a win partition). 

```

sudo cp /media/IPOD/TECZKA/MS\ Fonts/* . 

espace@acer-ubuntu:/usr/share/fonts/MS$ ls
arialbd.ttf  ebtmi5.ttf    georgiai.ttf  palabi.ttf    timroub.ttf
arialbi.ttf  ebtmi7.ttf    georgia.ttf   palab.ttf     timroui.ttf
ariali.ttf   ebtr10.ttf    georgiaz.ttf  palai.ttf     timrou.ttf
arial.ttf    ebtr5.ttf     impact.ttf    pala.ttf      trebucbd.ttf
ariblk.ttf   ebtr7.ttf     kartika.ttf   ply_____.ttf  trebucbi.ttf
comicbd.ttf  ebtsl10.ttf   l_10646.ttf   raavi.ttf     trebucit.ttf
comic.ttf    ebtsy10.ttf   latha.ttf     shruti.ttf    trebuc.ttf
courbd.ttf   ebtsy5.ttf    lsansdi.ttf   sylfaen.ttf   tunga.ttf
courbi.ttf   ebtsy7.ttf    lsansd.ttf    symbol.ttf    verdanab.ttf
couri.ttf    ebtti10.ttf   lsansi.ttf    tahomabd.ttf  verdanai.ttf
cour.ttf     ebttt10.ttf   lsans.ttf     tahoma.ttf    verdana.ttf
ebtbx10.ttf  estre.ttf     lucon.ttf     timesbd.ttf   verdanaz.ttf
ebtbx5.ttf   framdit.ttf   mangal.ttf    timesbi.ttf   vrinda.ttf
ebtbx7.ttf   framd.ttf     marlett.ttf   timesi.ttf    webdings.ttf
ebtex10.ttf  gautami.ttf   micross.ttf   times.ttf     wingding.ttf
ebtmi10.ttf  georgiab.ttf  mvboli.ttf    timroubi.ttf
espace@acer-ubuntu:/usr/share/fonts/MS$ sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 5 dirs
/usr/share/fonts/MS: caching, new cache contents: 79 fonts, 0 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 2 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/sazanami: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 51 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/ttf: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/espace/.fonts: skipping, no such directory
/usr/share/fonts/truetype/ttf-malayalam-fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/espace/.fontconfig: cleaning cache directory
fc-cache: succeeded


```
That sounds quite cool, especially 
```

/usr/share/fonts/MS: caching, new cache contents: 79 fonts, 0 dirs
```
which seems to indicate that the fonts in the directory I created were found and cached. 
However, when I open FF, it ***fails to render any windows font***, making much of the websites garbage. 
Am I doing something wrong? Any ideas?

---

