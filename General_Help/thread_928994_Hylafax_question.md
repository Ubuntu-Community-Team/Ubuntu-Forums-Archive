---
title: "Hylafax question"
date: 2008-09-24
forum: General Help
---

### Post by comprx on 2008-09-24
Hello, I'm attempting to setup a hylafax server for a friend. I installed and configured the modem just fine, but now I am not quite sure how to configure the server to take the incoming faxs and attach them to an email to him.

I already looked into this thread:
[http://ubuntuforums.org/showthread.php?t=888080&highlight=hylafax](http://ubuntuforums.org/showthread.php?t=888080&highlight=hylafax)

and i found something from one of it's links that MAY do what I am looking for.

> 
"Create the file etc/FaxDispatch (usually /var/spool/hylafax/etc/FaxDispatch) so that it contains the following lines:

	FILETYPE=tif;
	SENDTO=FaxMaster;

Substitute pdf or ps for tif as you desire. "


would I just replace "FaxMaster" with his email address?

---

### Post by comprx on 2008-09-24
a

---

