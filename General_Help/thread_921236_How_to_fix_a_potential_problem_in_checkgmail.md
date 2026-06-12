---
title: "How to fix a potential problem in checkgmail"
date: 2008-09-16
forum: General Help
---

### Post by karldiechmann on 2008-09-16
For quite some time, I had problems with [checkgmail]("http://checkgmail.sourceforge.net/") not working, with the following error message:
```
error parsing attribute name
attributes construct error
xmlParseStartTag: problem parsing attributes
Couldn't find end of Start Tag label_delay line 14 at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 370
A thread exited while 2 threads were running
```.

The problem is either with your preferences (~/.checkgmail/prefs.xml) or possibly also ~/.checkgmail/lang.xml.  When you add a label to be monitored by checkgmail, the default name is "[label name]".  This field is used as an attribute in the XML prefs.  So while "Work='300'" is a perfectly valid XML attribute, "[label name]='300'" is not.  (The 300 indicates how frequently the labe should be checked.)

Either removing the "[label name]" attribute or deleting prefs.xml should take care of the problem.

---

