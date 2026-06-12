---
title: "system-config-lvm"
date: 2015-02-02
forum: Hardware
---

### Post by lance bermudez on 2015-02-02
Trying to set up lvm with system-config-lvm and getting

The program 'system-config-lvm.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2618 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by weatherman2 on 2015-02-02
What operating system and version?  Server or desktop?

You can create LVM volumes with a few command lines in a terminal - it's not that hard.  What are you trying to do exactly?

---

### Post by lance bermudez on 2015-02-02
Lubuntu Ubuntu 14.04.1 LTS I have an old desktop with many hard drives to make one drive for storage. I have done the cli commands and keep getting messed up but was using the gui and it was working tell I set up my test drive then it was no go for the gui. Gui was crashing right after comming up.

[http://www.linuxquestions.org/questions/linux-general-1/lvm-gui-crashing-4175507127/](http://www.linuxquestions.org/questions/linux-general-1/lvm-gui-crashing-4175507127/) and [https://git.fedorahosted.org/cgit/system-config-lvm.git/commit/?id=c99d490707a8ccdc2f89d1dc062986b3d65649c1](https://git.fedorahosted.org/cgit/system-config-lvm.git/commit/?id=c99d490707a8ccdc2f89d1dc062986b3d65649c1) said to do the below
/usr/share/system-config-lvm/Volume_Tab_View.py on line 544

 def on_best_fit(self, obj):
      if (self.try_not_best_fit == True):
          return

change the above to the below

  def on_best_fit(self, obj):
      if (self.try_not_best_fit == True):
         if self.display_view.display != None:
             self.display_view.display.respect_smallest_selectable_width(False)
         return

---

