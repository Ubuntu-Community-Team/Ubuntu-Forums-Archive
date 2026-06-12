---
title: "python2.5-minimal problem after upgrade to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by eXt on 2009-11-03
Hi!

  After upgrade from Jaunty to Karmic Koala I have a problem with python2.5-minimal package. The problem was first reported during an upgrade. Now it is reported after system is started. I can't remove nor reinstall this package because I get:

```
E: python2.5-minimal: podproces installed post-installation script zwróci&#322; kod b&#322;&#281;du 2
```
which is in english:
```
E: python2.5-minimal: subprocess installed post-installation-script returned error code 2
```

Detailed error is:

```
Konfigurowanie python2.5-minimal (2.5.4-1ubuntu6) ...
Linking and byte-compiling packages for runtime python2.5...
/usr/lib/python2.5/site-packages/Onboard/KeyboardSVG.py:105: Warning: 'with' will become a reserved keyword in Python 2.6
Compiling /usr/lib/python2.5/site-packages/Onboard/KeyboardSVG.py ...
  File "/usr/lib/python2.5/site-packages/Onboard/KeyboardSVG.py", line 105
    with open(pane_svg_filename) as svg_file:
            ^
SyntaxError: invalid syntax

Errors were ignored.
update-binfmts: /var/lib/binfmts/python2.6 corrupt: out of binfmt data reading
package 
dpkg: b&#322;&#261;d przetwarzania python2.5-minimal (--configure):
 podproces installed post-installation script zwróci&#322; kod b&#322;&#281;du 2
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

After I fixed this error in KeyboardSVG.py I still get:

```
Konfigurowanie python2.5-minimal (2.5.4-1ubuntu6) ...
Linking and byte-compiling packages for runtime python2.5...
update-binfmts: /var/lib/binfmts/python2.6 corrupt: out of binfmt data reading
package 
dpkg: b&#322;&#261;d przetwarzania python2.5-minimal (--configure):
 podproces installed post-installation script zwróci&#322; kod b&#322;&#281;du 2
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

I didn't find anything valuable about such an error. There is a similiar report: [https://bugs.launchpad.net/ubuntu/+source/onboard/+bug/460389](https://bugs.launchpad.net/ubuntu/+source/onboard/+bug/460389) and some posts saying to use apt-get remove python2.5-minimal, purge, reinstall etc. But nothing works for me. Any ideas?

---

### Post by Cfossy2 on 2009-12-10
I also had a similar problem, whenever I tried to install any program, whether through Apt-get or synaptic i always get the same output: 
Errors were encountered while processing:
 python2.5-minimal
 python2.5
 python-gda
 python-gnome2-extras
 easycrypt
 python-gnome2-extras-dev
 python-gnome2-extras-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)

My problem is that I now cannot install anything without an error relating to python2.5 minimal coming up. There is also a problem with dependencies for python 2.5 minimal. How do I overcome this problem, any ideas would be gratefully accepted.

---

### Post by UN-BE-LIEV-ABLE Zenyatta! on 2009-12-31
I've just solved this issue (on my PC anyway :P).

Here's how I did it...

1. Open Nautlius with Super User permissions - sudo nautilus in terminal.
2. Browse to the folder giving you trouble...

```
update-binfmts: /var/lib/binfmts/python2.6 corrupt: out of binfmt data reading
package 

```3. My problem was a corrupt 2.5python-minimal file, it clearly showed up when I browsed to the folder. Delete this bad file, thats why you need sudo permissions.
4. Now DOWNLOAD the package from the web of the file you have just deleted, don't try and do it with Update Manager or re-install with Synaptic Package Manager 'coz it won't work.
5. Install it with 

```
sudo dpkg -i /..path to file../python2.5-minimal_2.5.2-15_amd64.deb
```

6. Run Synaptic Package Manager and choose Edit, Fix Broken Packages. 

After I did this my updates went straight through and saved me a complete re-build.

Hope this helps.

UZ.

---

