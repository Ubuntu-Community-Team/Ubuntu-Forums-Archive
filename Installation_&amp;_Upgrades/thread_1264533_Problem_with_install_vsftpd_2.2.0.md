---
title: "Problem with install vsftpd 2.2.0"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by mrmaster on 2009-09-12
Hello,

I gave myself root and did a "make". Everything went fine without any errors. After doing "make install" I get this error and i'm not sure how to fix it.

if [ -x /usr/local/sbin ]; then \
		install -m 755 vsftpd /usr/local/sbin/vsftpd; \
	else \
		install -m 755 vsftpd /usr/sbin/vsftpd; fi
if [ -x /usr/local/man ]; then \
		install -m 644 vsftpd.8 /usr/local/man/man8/vsftpd.8; \
		install -m 644 vsftpd.conf.5 /usr/local/man/man5/vsftpd.conf.5; \
	elif [ -x /usr/share/man ]; then \
		install -m 644 vsftpd.8 /usr/share/man/man8/vsftpd.8; \
		install -m 644 vsftpd.conf.5 /usr/share/man/man5/vsftpd.conf.5; \
	else \
		install -m 644 vsftpd.8 /usr/man/man8/vsftpd.8; \
		install -m 644 vsftpd.conf.5 /usr/man/man5/vsftpd.conf.5; fi
if [ -x /etc/xinetd.d ]; then \
		install -m 644 init.d/vsftpd /etc/init.d/vsftpd; fi

Thank you

---

### Post by ahbart on 2009-09-12
I have no answer for you, because you don't have a question ;-)
Just a suggestion: have a look at gadmin-proftpd. It's in the ubuntu repository.

---

### Post by mrmaster on 2009-09-13
> **ahbart said:**
> I have no answer for you, because you don't have a question ;-)
Just a suggestion: have a look at gadmin-proftpd. It's in the ubuntu repository.


After I do a "make install" why isn't it installing the program? What does that error message mean exactly?

I've new to compiling and installing programs in linux from what i understand you "make" to compile the program and then "make install" to install it in your box.

---

### Post by traylorre on 2009-09-27
Good work, you installed it correctly.

You are looking an 'echo' of the internal logic of the script.  Normally, this is not shown, but in this script it is done for your convenience.

I recently went through your steps.  I had the same output, and my vsftpd is working.

Cheers.

---

