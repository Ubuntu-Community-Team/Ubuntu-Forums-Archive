---
title: "Theme selector complains about missing GTK+ theme engine 'smooth'"
date: 2008-11-19
forum: General Help
---

### Post by sarte on 2008-11-19
After I updated my system to itrepid I've been having following error message from my theme selector (System --> appearance --> theme).

```
Required GTK+ theme engine 'smooth' is not installed
```

It is a problem of one new theme that was included in intrepid update.

Tried to install smooth with apt and got an error

```
sudo apt-get install gtk2-engines-smooth
```

but the package was changed:

```
However the following packages replace it:
  gtk2-engines
E: Package gtk2-engines-smooth has no installation candidate
```

And of course gtk2-engines was already installed. So of course I tried following

```
sudo apt-get remove gtk2-engines
sudo apt-get install gtk2-engines
```

And when that didn't work I even tried to build it from the package I found from art.gnome.org and I ended up having a following error message on my screen:


```
checking for gtk+-2.0 >= 2.4.0... configure: error: GTK+-2.4 is required
```


Anyone has any ideas how to fix this?

---

### Post by Fejker on 2008-12-02
I have the same problem. I want to use some of the nice smooth themes.

Any help would be very welcome.

---

### Post by yas1909 on 2008-12-03
same here , i am having the same problem too..anybody please help !!!

---

### Post by loomsen on 2008-12-03
```
sudo apt-get install gtk-smooth-themes
```

---

### Post by Fejker on 2008-12-03
```
fejker@fejker-laptop:~$ sudo apt-get install gtk-smooth-themes
[sudo] password for fejker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk-smooth-themes is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Nope, doesn't work. The theme manager still complains about the missing smooth engine.

---

### Post by fsando on 2008-12-09
As far as I can see the gtk2-engines-smooth must be considered obsolete by Ubuntu team. Last official release appears to be in Dapper, in hardy it is listed as conflicting with gtk2-engines.

See [here]("https://launchpad.net/ubuntu/hardy/i386/gtk2-engines/1:2.14.3-0ubuntu2") and [here]("https://launchpad.net/+search?field.text=gtk2-engines-smooth").

I haven't been able to find gtk2-engine-smooth anywhere but from the links above it's probably not advisable to install it anyway.

I don't know how this works but my feeling is that when a theme needs a certain engine which is not available that engine would be a dependency that isn't met.

UPDATE (5min later):
In gnome-art: the menu
Art > Other themes > GTK+ Engines
offers among other engines also the smooth engine for which you can download the source. The source is from 2004 which sort of confirms that it's deprecated.

---

### Post by yas1909 on 2008-12-11
but even though that the system is ask for GTK+ but still the theme works, which is one of the reason which am not complaining, just wanted to know if there is a solution to it.. but i do have a problem tho,instead of an apple icon i still have the gnome icon on my taskbar and also when the the actual linux is booting up why doesnt the Apple logo come up ?? but the logging page is the apple version one tho ..
any help would be the most welcome

---

### Post by Fejker on 2008-12-11
The theme needs the smooth engine only for particular parts so yes it displays the modified parts which don't need the smooth engine but fails to do so with the parts where the smooth engine is needed.

That's my explanation because the themes I want to use don't look right in any way.

---

### Post by the yawner on 2008-12-11
As of Hardy, smooth is already part of the package gtk2-engines and thus there is no need to have a separate installation. Quoted from [here]("http://packages.ubuntu.com/hardy-updates/gtk2-engines"):
> 
This package contains the "engines" that hide behind the themes for GTK+ and GNOME applications. They redefine the way GTK+ widgets are drawn. The package includes the following engines:

 * Clearlooks, the default GNOME theme, based on Bluecurve;
 * Crux, formerly known as the Eazel engine;
 * High contrast, which is used by some accessibility themes;
 * Industrial, the famous engine from Novell (formerly Ximian);
 * LighthouseBlue, another engine based on Bluecurve;
 * Metal, which gives a metallic look;
 * Mist, a flat and high performance engine;
 * Redmond95, which provides a look similar to that of Windows;
 * **Smooth**, which is used by many themes as being nice, fast and
   configurable;
 * ThinIce.


Comparing the same package in [Intrepid]("http://packages.ubuntu.com/intrepid/gtk2-engines"):
> 
This package contains the "engines" that hide behind the themes for GTK+ and GNOME applications. They redefine the way GTK+ widgets are drawn. The package includes the following engines:

 * Clearlooks, the default GNOME theme, based on Bluecurve;
 * Crux, formerly known as the Eazel engine;
 * High contrast, which is used by some accessibility themes;
 * Industrial, the famous engine from Novell (formerly Ximian);
 * LighthouseBlue, another engine based on Bluecurve;
 * Metal, which gives a metallic look;
 * Mist, a flat and high performance engine;
 * Redmond95, which provides a look similar to that of Windows;
 * ThinIce.


For some reason smooth is no longer part of the package. And installing the engine from other repos would conflict with gtk2-engine and thus is unadvisable. Try filing a bug report to query why the engine was removed.

---

### Post by MonkeeSage on 2009-02-02
Workaround (downloads an older .deb from launchpad to temporary directory, extracts it, copies the two needed files, removes temporary directory):

```

mkdir tmpdir
cd tmpdir

wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_i386.deb

ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb && \
\
tar xf data.tar.gz && \
\
sudo cp usr/share/gtk-engines/smooth.xml \
    /usr/share/gtk-engines && \
\
sudo cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so \
    /usr/lib/gtk-2.0/2.10.0/engines

cd ../
rm -rf tmpdir

```

NB. The entire code block above can be copied and pasted into a terminal--each line doesn't need to be entered separately.

---

### Post by superman_is_deady on 2009-02-03
yeach... i see same that happen to my ubuntu...
Thx...

---

### Post by zoey_s on 2009-03-21
> **MonkeeSage said:**
> Workaround (downloads an older .deb from launchpad to temporary directory, extracts it, copies the two needed files, removes temporary directory):

```

mkdir tmpdir
cd tmpdir

wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_i386.deb

ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb && \
\
tar xf data.tar.gz && \
\
sudo cp usr/share/gtk-engines/smooth.xml \
    /usr/share/gtk-engines && \
\
sudo cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so \
    /usr/lib/gtk-2.0/2.10.0/engines

cd ../
rm -rf tmpdir

```

NB. The entire code block above can be copied and pasted into a terminal--each line doesn't need to be entered separately.

Thank You, Thank You.....Works Perfectly!!  zoey

---

### Post by dbbolton on 2009-03-21
> **MonkeeSage said:**
> Workaround (downloads an older .deb from launchpad to temporary directory, extracts it, copies the two needed files, removes temporary directory):

```

mkdir tmpdir
cd tmpdir

wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_i386.deb

ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb && \
\
tar xf data.tar.gz && \
\
sudo cp usr/share/gtk-engines/smooth.xml \
    /usr/share/gtk-engines && \
\
sudo cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so \
    /usr/lib/gtk-2.0/2.10.0/engines

cd ../
rm -rf tmpdir

```

NB. The entire code block above can be copied and pasted into a terminal--each line doesn't need to be entered separately.
Thanks. I'm running a 64 bit system, and I used this deb: [http://packages.ubuntu.com/hardy/amd64/gtk2-engines/download](http://packages.ubuntu.com/hardy/amd64/gtk2-engines/download)

It appears to work fine.

---

### Post by tjbonzo on 2009-03-29
I wasn't set on using smooth - I just wanted the error messages to go away. I went to:
System->Preferences->Appearances
And changed from a "Custom" theme to one of the standard themes. No more "smooth" messages.

---

### Post by fabdango on 2009-08-24
> **MonkeeSage said:**
> Workaround (downloads an older .deb from launchpad to temporary directory, extracts it, copies the two needed files, removes temporary directory):

```

mkdir tmpdir
cd tmpdir

wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_i386.deb

ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb && \
\
tar xf data.tar.gz && \
\
sudo cp usr/share/gtk-engines/smooth.xml \
    /usr/share/gtk-engines && \
\
sudo cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so \
    /usr/lib/gtk-2.0/2.10.0/engines

cd ../
rm -rf tmpdir

```NB. The entire code block above can be copied and pasted into a terminal--each line doesn't need to be entered separately.
It worked perfectly and the engine is awesome! Thank you very much.

---

### Post by SugarMan on 2010-03-16
> **MonkeeSage said:**
> Workaround (downloads an older .deb from launchpad to temporary directory, extracts it, copies the two needed files, removes temporary directory):

```

mkdir tmpdir
cd tmpdir

wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_i386.deb

ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb && \
\
tar xf data.tar.gz && \
\
sudo cp usr/share/gtk-engines/smooth.xml \
    /usr/share/gtk-engines && \
\
sudo cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so \
    /usr/lib/gtk-2.0/2.10.0/engines

cd ../
rm -rf tmpdir

```NB. The entire code block above can be copied and pasted into a terminal--each line doesn't need to be entered separately.

Thank you! It works well.

---

