---
title: "Temperature Control in Ubuntu 8.04"
date: 2008-08-05
forum: Hardware
---

### Post by JazzyPenguin on 2008-08-05
Hi all, and thanks to the community for getting me this far.  I have recently ditched Windoze for Ubuntu 8.04 LTS on a Lenovo 3000 N200 0769.   With the help of community post have successfully installed sound and video and solved a number of issues.  I'm impressed so far but have a problem that is concerning me greatly.  The laptop seems to run very hot.  I can get the nvidia and hddtemp applets to report on video and HD temps but cannot get the duo 2 core CPU to coopertate with the Gnome Sensors Applet.  Any help or pointers greatly appreciated.  I'm concerned running ubuntu as-is is slowly frying my new laptop.  But, I desprately don't want to go make to Windoze.

---

### Post by NilsE on 2008-08-05
If you haven't already install lm-sensors which should detect all sensors.

---

### Post by JazzyPenguin on 2008-08-05
> **NilsE said:**
> If you haven't already install lm-sensors which should detect all sensors.

Thanks NilsE.   I do have lm-sensors installed.  Running ```
sudo sensors
``` in Terminal I get "no sensors found".   Running ```
sudo sensors-detect
``` and answering the questions with the default answers I get the same answer i.e. no sensors detected.  I have of course being looking around in the forums etc and it seems getting ACPI to work may be the answer. However, lsmod does not list ibm-acpi (probably the most relevant module listed on the Gnome Sensors Applet Website).  I have not been able to find an easy to follow install for this module.

---

### Post by doas777 on 2008-08-05
> **JazzyPenguin said:**
> Thanks NilsE.   I do have lm-sensors installed.  Running ```
sudo sensors
``` in Terminal I get "no sensors found".   Running ```
sudo sensors-detect
``` and answering the questions with the default answers I get the same answer i.e. no sensors detected.  I have of course being looking around in the forums etc and it seems getting ACPI to work may be the answer. However, lsmod does not list ibm-acpi (probably the most relevant module listed on the Gnome Sensors Applet Website).  I have not been able to find an easy to follow install for this module.

check [this thread]("http://ubuntuforums.org/showthread.php?t=2780") out. you have to run the script to create/detect your sensor objects before they can be polled.

good luck

---

### Post by JazzyPenguin on 2008-08-06
> **doas777 said:**
> check [this thread]("http://ubuntuforums.org/showthread.php?t=2780") out. you have to run the script to create/detect your sensor objects before they can be polled.

good luck

Thanks Doas777 tried it out but still no joy.   After following the instructions sensors-detect still returns no sensors found.   I have found patches for ibm-acpi does anyone know how to apply these patches?

---

### Post by JazzyPenguin on 2008-10-25
An update.   My problem is solved by undating to 8.10 release candidate.  Installed lm-sensors, ran sensors-detect.  Followed default answers to all questions.  Sensors-detects detects intel thermal sensors and outputs text to be added to /etc/modules.

In my case the coretemp module.

Restart and there they are!!

Brilliant....

---

