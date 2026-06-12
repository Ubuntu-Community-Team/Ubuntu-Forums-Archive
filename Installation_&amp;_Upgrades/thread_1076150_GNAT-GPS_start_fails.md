---
title: "GNAT-GPS start fails"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by georg123 on 2009-02-21
Hi All,

I have installed GNAT and GNAT-GPS on Ubuntu 8.04 (Hardy Heron) using synaptic paket management system.

When typing gnat-gps on the console I get the error message:

raised SYSTEM.ASSERTIONS.ASSERT_FAILURE : glib-graphs.ads:352

What could the problem be and how can I fix that?

Best regards

Georg

---

### Post by skimwpi on 2009-02-28
I don't have 8.04 but I do have 8.10 (Intrepid) and I do have gnat-gps installed and running although I can't say that it's running fine.

I can get into the IDE but it starts up with the following error/warning...
******************************************************************
[2009-02-28 15:16:18] Error while parsing /usr/share/gps/plug-ins/changelog.xml
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/share/gps/plug-ins/ada_support.py", line 11, in <module>
    import os_utils, gnat_switches
ImportError: No module named gnat_switches
[2009-02-28 15:16:18] There are several startup scripts with the same name: methods.py
Not loading: /usr/share/gps/library/methods.py
[2009-02-28 15:16:18] There are several startup scripts with the same name: gnatpsta.py
Not loading: /usr/share/gps/library/gnatpsta.py
******************************************************************

Has anyone else encountered this? 

I seem to have problems adding files to a project. As a result, I have been using GNAT-GPS to write my Ada code for the color formatting feature but compiling with gnatmake command on the terminal.

---

### Post by mathieud on 2009-10-22
Hello,

I don't know if you still need help but I was fighting with this problem and just found a solution.

Apparently, there is no way to make this version work (see [http://groups.google.com/group/comp.lang.ada/browse_thread/thread/ab52b3b75f6b8538]("http://groups.google.com/group/comp.lang.ada/browse_thread/thread/ab52b3b75f6b8538") for instance).
So the best solution is to download GNAT GPL Edition from Adacore website: [https://libre.adacore.com/libre/download/]("https://libre.adacore.com/libre/download/").
You will need to create an account (it's free and I never had any trouble or spam).

Then just download the files in the "GNAT GPL" folder (it contains the GNAT toolchain and GPS).

Installation is very easy. Just decompress the file in some directory (the downloaded file may contain other archives so you will need to decompress them too). At some time you will find a script called "doinstall". Just run it (with sudo). Alternatively, read the INSTALL file.

If you are a bit used to installing software without synaptic it's very easy.

Hope that helps,
Mathieu

---

