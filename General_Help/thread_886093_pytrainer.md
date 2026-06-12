---
title: "pytrainer"
date: 2008-08-10
forum: General Help
---

### Post by bmenge on 2008-08-10
I had pytrainer working on my system with a garmin edge 205.  I had only transferred data once then tried to again later and pytrainer froze. I then did a force quit and tried to reopen the terminal from the launcher, now pytrainer will not start.  I get the basic gui and then it stops with no data in the fields.  I tried to start pytrainer from the terminal and this is as far as it gets.  I have tried to reboot and did a ps aux command to see if it was running somewhere and not behaving correctly, I didn't noticed anything though.

```
brian@brian-desktop:~$ pytrainer
location: /usr/lib/xulrunner-1.9.0.1/libxpcom.so 
before 3
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
Loading Plugin Garmin
No Active Extensions
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/pytrainer/gui/windowmain.py", line 499, in on_page_change
    self.parent.refreshGraphView(self.selected_view)
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 139, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/usr/lib/python2.5/site-packages/pytrainer/gui/windowmain.py", line 187, in actualize_dayview
    average = distance/(timeinseconds/60/60)
ZeroDivisionError: float division
Traceback (most recent call last):
  File "/usr/bin/pytr", line 44, in <module>
    main()
  File "/usr/bin/pytr", line 41, in main
    pytrainer = pyTrainer(None, data_path)
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 78, in __init__
    self.windowmain.on_calendar_selected(None)
  File "/usr/lib/python2.5/site-packages/pytrainer/gui/windowmain.py", line 537, in on_calendar_selected
    self.parent.refreshGraphView(self.selected_view)
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 139, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/usr/lib/python2.5/site-packages/pytrainer/gui/windowmain.py", line 187, in actualize_dayview
    average = distance/(timeinseconds/60/60)
ZeroDivisionError: float division
```
I did reinstall the application as well since I had only connected the garmin once.  This did nothing to the way pytrainer started.

---

### Post by raketten on 2009-03-01
I have the exact same problem!:(
I have tryed to remove pytrainer completely and reinstall, reboot (as it was windows!) but no luck.

---

### Post by lingenfr on 2009-04-11
I was running pytrainer from the repository the developer was making available. Unfortunately, he took down his repository and when I looked I saw I was several versions behind. I used apt and removed the previous version. Then I downloaded the new version. The site only lists the dependencies for Fedora and the package names are different for ubuntu. I think I sorted them out, but maybe I missed one. Pytrainer launches then hangs. When launched from the command line, here is what I get:

---------------
lingenfr@ubuntu:~/Desktop/pytrainer-1.6.0.7$ ./pytrainer.sh -i
location: /usr/lib/xulrunner-1.9.0.8/libxpcom.so 
before 3
*** Log level set to INFO ***
this function is obsolete, use getValue instead
2009-04-11 10:24:02,832|INFO|main|migrationCheck|Old version: 1.6.0.7 | New version: 1.6.0.7
2009-04-11 10:24:04,415|INFO|plugins|loadPlugin|Loading plugin Garmin Heart Rate
No Active Extensions
Traceback (most recent call last):
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 690, in on_page_change
    self.parent.refreshGraphView(self.selected_view)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 195, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 248, in actualize_dayview
    if configuration.getValue("pytraining","prf_us_system") == "True":
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/lib/xmlUtils.py", line 79, in getValue
    value = root.attributes[variable].value
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 529, in __getitem__
    return self._attrs[attname_or_tuple]
KeyError: 'prf_us_system'
Traceback (most recent call last):
  File "pytrainer.py", line 54, in <module>
    main(sys.argv[1:])
  File "pytrainer.py", line 50, in main
    pytrainer = pyTrainer(None, data_path)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 118, in __init__
    self.windowmain.on_calendar_selected(None)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 732, in on_calendar_selected
    self.parent.refreshGraphView(self.selected_view)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 195, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 248, in actualize_dayview
    if configuration.getValue("pytraining","prf_us_system") == "True":
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/lib/xmlUtils.py", line 79, in getValue
    value = root.attributes[variable].value
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 529, in __getitem__
    return self._attrs[attname_or_tuple]
KeyError: 'prf_us_system'
------------------------

It gets to this point and hangs until I hit Cntl-C to kill it. Does anyone have this working. If so, you would do the community a great service if:

Good: Publish the list of Ubuntu dependencies
Better: Place a working deb up on getdeb
Best: Set up a repository for pytrainer/Intrepid

---

### Post by dgranda on 2009-04-12
> **lingenfr said:**
> I was running pytrainer from the repository the developer was making available. Unfortunately, he took down his repository and when I looked I saw I was several versions behind. I used apt and removed the previous version. Then I downloaded the new version. The site only lists the dependencies for Fedora and the package names are different for ubuntu. I think I sorted them out, but maybe I missed one. Pytrainer launches then hangs. When launched from the command line, here is what I get:

---------------
lingenfr@ubuntu:~/Desktop/pytrainer-1.6.0.7$ ./pytrainer.sh -i
location: /usr/lib/xulrunner-1.9.0.8/libxpcom.so 
before 3
*** Log level set to INFO ***
this function is obsolete, use getValue instead
2009-04-11 10:24:02,832|INFO|main|migrationCheck|Old version: 1.6.0.7 | New version: 1.6.0.7
2009-04-11 10:24:04,415|INFO|plugins|loadPlugin|Loading plugin Garmin Heart Rate
No Active Extensions
Traceback (most recent call last):
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 690, in on_page_change
    self.parent.refreshGraphView(self.selected_view)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 195, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 248, in actualize_dayview
    if configuration.getValue("pytraining","prf_us_system") == "True":
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/lib/xmlUtils.py", line 79, in getValue
    value = root.attributes[variable].value
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 529, in __getitem__
    return self._attrs[attname_or_tuple]
KeyError: 'prf_us_system'
Traceback (most recent call last):
  File "pytrainer.py", line 54, in <module>
    main(sys.argv[1:])
  File "pytrainer.py", line 50, in main
    pytrainer = pyTrainer(None, data_path)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 118, in __init__
    self.windowmain.on_calendar_selected(None)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 732, in on_calendar_selected
    self.parent.refreshGraphView(self.selected_view)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/main.py", line 195, in refreshGraphView
    self.windowmain.actualize_dayview(record_list)
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/gui/windowmain.py", line 248, in actualize_dayview
    if configuration.getValue("pytraining","prf_us_system") == "True":
  File "/home/lingenfr/Desktop/pytrainer-1.6.0.7/pytrainer/lib/xmlUtils.py", line 79, in getValue
    value = root.attributes[variable].value
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 529, in __getitem__
    return self._attrs[attname_or_tuple]
KeyError: 'prf_us_system'
------------------------

It gets to this point and hangs until I hit Cntl-C to kill it. Does anyone have this working.

Hi there,

I am one of the admins of [pytrainer project]("http://sourceforge.net/projects/pytrainer/"). If you have any problem with it, it is much faster to post it to the [distribution list]("http://sourceforge.net/mailarchive/forum.php?forum_name=pytrainer-devel") in order to have an answer from people involved in the project as we usually don't joins distribution specific forums. Actually I was looking for a deb version of the latest release (there is one guy interested in making the deb version official for Debian) when I saw this post.

Anyway, it's a good idea first to check mentioned list to see if your question has been answered before. Some people work on development versions retrieved from svn and most problems appear there. In this case, please have a look at [this thread]("http://sourceforge.net/mailarchive/message.php?msg_name=1220218350.1598.39.camel%40bagend.luchko.ca").

> If so, you would do the community a great service if:

Good: Publish the list of Ubuntu dependencies
Better: Place a working deb up on getdeb
Best: Set up a repository for pytrainer/Intrepid

We are working on this, thanks for feedback ;). Ideal situation would be to publish deb version on SF page and then send the binary for approval to integrate it into official distribution repositories.

Regards,

David

---

### Post by lingenfr on 2009-04-18
Unfortunately the pytrainer folks only offer forums for bugs and feature requests and then developer mailing lists. Would be nice if the would have a forum just for questions. I got the latest pytrainer, but the only way I can run it is to go in with a terminal. There are a number of files and I really don't want to clutter up my /usr/bin directory. What is a good way to set this up so that I can put a menu entry, etc like I used to get when they offered a package in their repository? Thanks.

---

### Post by lars.modig on 2009-05-04
Hi Ligenfr...

Did you make your pytrainer running? I've got the same problem and has a hard time figure it out. Earlier I've run the deb file from pytrainer homepage, but it looks like they removed that now. Would realy appr. if someone could put a new deb up.

Br,

Lars

---

### Post by lingenfr on 2009-05-04
I have not gotten mine running any way other than using terminal. I expect that I needed to change a setting before I compiled it. It makes absolutely no sense why they couldn't put the deb up on getdeb or one of the filesharing services. I can understand if they lost their hosting or were exceeding their bandwidth quotas. As there is nothing similar in the repositories, it would be nice to see it added. I posted to the mailing list and didn't get anything useful. The suggestion(s) I got were things I had already tried. I really don't want to crap up my /usr/bin and can't tell what are the absolute minimum files for it to run. In the interim, I am continuing to run the Garmin app in virtualbox. I've tried it under wine and it was a no-go.

---

### Post by dgranda on 2009-05-17
We are in our way to make pytrainer available from Debian official repositories (unstable): [http://packages.debian.org/unstable/main/pytrainer](http://packages.debian.org/unstable/main/pytrainer)

Did anyone out there give it a try?

---

### Post by lingenfr on 2009-05-17
The iceweasel dependency creates a problem for us *buntu users as it is not in the repos and not a snap to install. I will have a look at it. I and I expect most of us use the default Firefox. IANAP and don't understand why apps that use the browser can't work with any of the mozilla based browsers.

I tried installing the debian iceweasel package and it would not install with gdebi. The ubuntuguide says that Iceweasel is provided by the iceape-browser package. I installed that, but the dependency still is not satisfied.

---

### Post by dgranda on 2009-05-21
Please check also [https://launchpad.net/~kevin-pheared/+archive/ppa](https://launchpad.net/~kevin-pheared/+archive/ppa)

---

### Post by ozonito on 2009-05-21
Hi, thanks for .deb (Voalá!!!) of pytrainer. Depends it's OK, but not started yet to me. This my bash:

Traceback (most recent call last):
  File "/usr/bin/pytrainer", line 38, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/lib/python2.6/dist-packages/pytrainer/main.py", line 45, in <module>
    from extensions.googlemaps import Googlemaps
  File "/usr/lib/python2.6/dist-packages/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed

Thanks a lots from Canary Island, and excuse my poor english. 
System AMDx64 with Jaunty.

---

### Post by kseise on 2010-01-06
I have a copy of pyTrainer installed from the Karmic Repositories.  I tried to add swimming as a sport and was informed that I had to go to the project website to download the met.pdf to get some of the information to add for the sport.  The link goes to the OLD project website.  I have posted a request to the devel mailing list, but have not heard any response.

Does anyone have a copy of the PDF that you can send me?  Or can you post a link to the correct download site?

---

### Post by kseise on 2010-01-12
Amazing.  Pytrainer seems to have uninstalled itself from both my netbook and desktop.  Also, all of my distances are wiped out, but my other settings stayed.  Any idea what happened?

---

