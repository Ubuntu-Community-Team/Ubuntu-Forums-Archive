---
title: "Paperport software linux equivalent"
date: 2005-11-26
forum: General Help
---

### Post by Remmelas on 2005-11-26
Is there a replacement available that simulates paperport's functionality?  In particular, i'm looking for the ability to capture and manage easily text from web pages and other docs.  

--Thanks

---

### Post by loser72555 on 2006-07-14
Look over on sourceforge for a project called "maxview"

There is a Kiwi (New Zealander) who runs the project.  Very nice guy and very helpful.

---

### Post by perspectoff on 2008-04-14
No, there isn't.

MaxView (the new Zealand project) is rudimentary and doesn't really work very well.

Also, MaxView has trouble over the network (for Samba mounted directories).

Scansoft has no interest in writing Paperport for Linux, according to the email reply they sent me.

(If you really want Paperport, consider supporting the Wine project (or the commercial Cedega) to enable Paperport. (Note: In 2008 Wine dropped support for Paperport. Not enough interest.))

The other alternative if you really want Paperport is to run a VM machine (such as Virtualbox) on Linux, install a Windows OS (98SE or XP) on the VM, then install Paperport on the virtual machine. It's a lot of effort, though. Worth it, if you use a lot of other M$ Windows programs, though.

Xsane does not do what Paperport (or even MaxView) do. It is mostly just a scanner program.

Gnome and KDE are getting closer all the time to Paperport's full functionality, though -- probably 2 more versions of Gnome and KDE and they will work nearly identically.

Interestingly, Paperport (version 9) and Quicken are the only two programs keeping me tied to Windows XP in my small business.

However, Paperport 9 doesn't work with Windows Vista (the printer drivers are incompatible), and Paperport versions 10 and 11 are slow and bug-ridden.

---

### Post by perspectoff on 2008-04-14
Knowledge Tree is the closest (and probably best) replacement for PaperPort, if you want a robust document management system.

You can purchase a commercial "Plus" Edition of Knowledge Tree, which is (March 2008) currently $140/user per year.

There is a "Community" edition of Knowledge Tree, which is also very powerful and has won awards in 2007. Look on wikipedia for Knowledge Tree Community edition for the location of the downloads, as Knowledge Tree itself only points to its commercial edition.

In 2007, they added web-based content management as well, a la Drupal, Joomla, and Plone.

---

### Post by jdavis72 on 2008-06-16
> **Remmelas said:**
> Is there a replacement available that simulates paperport's functionality?  In particular, i'm looking for the ability to capture and manage easily text from web pages and other docs.  

--Thanks

Try gscan2pdf, it's in the repos. I too use Paperport, previously for my business, and also for my personal bills, etc. (trying to create a paperless office). The main benefits I see with Paperport is it creates a single window for creating and managing pdf's, and then searching the metadata when needed. Gscan2pdf will create the pdf's, including multipage docs, and let you enter all the metadata you need. I create a seperate directory for these docs, with subdirectories based on year and month. Searching through the metadata is then possible with strigi, beagle, etc. I agree it would be nice to have a similar prog like Paperport for gnu/linux on a single computer without needing mysql, etc., instead of using 2 different progs like this. But until then, or I learn to program myself :), this is what I recommend for personal use. Just my 2 cents.

Jeremy

---

