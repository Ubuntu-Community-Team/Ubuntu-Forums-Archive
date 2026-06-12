---
title: "Unable to get any (Sun) Java (32 bit or 64 bit) working in 64 bit Intrepid"
date: 2008-11-23
forum: General Help
---

### Post by Bluebell392 on 2008-11-23
I am unable the get Sun Java to work with 64 bit Intrepid, either the 32 bit version or the 64 bit version. I have tried installing from the repositories, from Java's website, everywhere. well, it installs, it works with .jar files, but it doesn't work in Firefox.

---

### Post by Pijits_1 on 2008-11-23
Have you tried installing open-jdk through synaptic?

Had the same sort of problem and this fixed it but if you have installed and tried it already I'm not sure what the problem could be :confused:

---

### Post by Bluebell392 on 2008-11-23
I'll try that, thanks.

---

### Post by Bluebell392 on 2008-11-23
Hmmm, it doesn't seem to work. It appears to be installed, and the java intrepeter works, but it doesn't appear to Firefox. Prehaps the plugin for Fireefox wasn't copied/linked correctly?

---

### Post by Pijits_1 on 2008-11-23
Don't think so, Do you have the GCJ Web Browser Plugin version 0.96.1. You can find it in synaptic as well or sudo apt-get install gcjwebplugin.

Its used to execute java applets, should solve your problem under firefox

---

### Post by Bluebell392 on 2008-11-23
NOW let's try it.

---

### Post by Bluebell392 on 2008-11-23
Okay, it shows up in  Firefox's about;plugins list, but some of the Java applets won't load. So now the question is, where are the logs, if any, for the plugin?

---

