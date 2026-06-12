---
title: "can't run system-config-printer"
date: 2009-10-05
forum: Hardware
---

### Post by beakdan on 2009-10-05
Hey folks-

I'm currently running Jaunty, and not able to install printers at the moment.  I think this started when I copied over my home folder from a backup; i remember doing something screwy that time and having a few problems getting all my files straight (this was a few months ago).

As of right now, clicking:
System > Administration > Printing

causes a window to popup (titled "Printer configuration - localhost"), and then immediately close itself.

Entering "system-config-printer" from the command line produces this:

/home/dan/.printer-groups.xml:1: parser error : Document is empty

^
/home/dan/.printer-groups.xml:1: parser error : Start tag expected, '<' not found

^
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/XmlHelper.py", line 37, in __init__
    self.xml_doc = libxml2.parseFile (self.group_file_name)
File "/var/lib/python-support/python2.6/libxml2.py", line 1279, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
parserError: xmlParseFile() failed
Continuing anyway..
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 6757, in <module>
    focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 6705, in main
    print_test_page, focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 565, in __init__
    self.groups_pane = GroupsPane ()
  File "/usr/share/system-config-printer/GroupsPane.py", line 144, in __init__
    for group_name, group_node in xml_helper.get_static_groups ():
  File "/usr/share/system-config-printer/XmlHelper.py", line 68, in get_static_groups
    return self.__parse_groups ("static-group")
  File "/usr/share/system-config-printer/XmlHelper.py", line 54, in __parse_groups
    current = self.xml_doc.getRootElement ().children
AttributeError: 'NoneType' object has no attribute 'getRootElement'

While this is happening, a window pops up titled "System-Config-Printer", but immediately closes itself.

It seems obvious that there's a problem with a file being empty that shouldn't be.  I tried fixing by removing and then reinstalling "system-config-printer-gnome".  I found no change in behavior.

Any help is appreciated.

Dan

---

### Post by dummy910 on 2009-10-05
Does the account your trying to manage the printer(s) with have authorization to do so via ```
**sudo users-admin**
```

---

### Post by beakdan on 2009-10-05
I checked, and yes, that account is authorized to configure printers (and I have in the past with no problems).

I also see the same behavior when running "sudo system-config-printer"

---

### Post by dummy910 on 2009-10-05
I've never run into this one, so I'm gonna guess it's a python issue(?) 

Are there several different pythons running-sleeping in your Systems>Administrator>System-Monitor? If so, I would kill them all and re-attempt the launch of the printer-config.

---

### Post by beakdan on 2009-10-05
There was only one instance of Python running.  Clicking "System > Administration > Printing" caused another instance to open, then close.

Killing the already-running Python instance, then clicking "S > A > Printing" produced the same result.

My guess is that in the backup process, I screwed up the ".printer-groups.xml" file (in my home folder).  Currently that file is blank.  Could you take a look at that file?  I'm not sure what should be in there, but if it's simple, could you post it here?  Maybe I can fix that file and thus make Python happy...

Thank again,
Dan

---

### Post by dummy910 on 2009-10-06
Try either renaming or deleting your **/home/[COLOR=red]youraccountname[/COLOR]/.printer-groups.xml** file as to let the system start from scratch with a new xml file.

---

### Post by beakdan on 2009-10-06
That worked, thanks!

---

### Post by dummy910 on 2009-10-06
Great!
Please mark this thread solved **beakdan** ;)

---

