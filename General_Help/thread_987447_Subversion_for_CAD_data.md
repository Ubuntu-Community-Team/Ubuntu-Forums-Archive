---
title: "Subversion for CAD data??"
date: 2008-11-19
forum: General Help
---

### Post by hambone79 on 2008-11-19
I'm looking for some revision control software to manage my Pro/E files and I have heard about people using Subversion for this. I'm a little confused about some of the details about subversion, so I'm hoping someone with experience can help me with the following questions:

1. Can subversion handle binary data or can it only be used with source code?
2. If I check out several files from my repository and update one of them (i.e. checking out all parts of an assembly but only updating one or two parts) will subversion allow me to only check in the parts that changed? Also, if I try to check in all the files is it intelligent enough to ignore the files that didn't change?
3. Can I setup subversion to dump the latest revision of all of my models to a read only directory that I can access with Pro/Engineer? This is a common practice in corporate CAD environments...the latest version of the CAD data is placed in a read only share...any files that need to be changed are checked out of the CAD management system while the remaining files are pulled from the read only share. This reduces the need to check-out/check-in things like standard hardware that is used in more than one assembly.

If anyone can answer some or all of these question I would appreciate it.

---

### Post by hambone79 on 2008-11-22
Anyone? Even if you don't use it for CAD data, is there anyone out there that has used Subversion for something other than source code?

---

### Post by DonQuichote on 2008-11-22
> **hambone79 said:**
> I'm looking for some revision control software to manage my Pro/E files and I have heard about people using Subversion for this. I'm a little confused about some of the details about subversion, so I'm hoping someone with experience can help me with the following questions:

1. Can subversion handle binary data or can it only be used with source code?

Subversion can handle binary data just fine. In fact, it only handles binary data and has some added features to "correct" for certain text formats (like line endings). There is only one problem: diff vierwers and diff editors for binary formats are rare, and a merge on a binary format may not make as much sense as on a text format.

I have my QCAD files all in subversion, but those are DXF files and therefore texts.

I also have word processor documents, images, compressed XML, etc. in subversion. If you are working with more than one person on a binary file and if that binary file cannot safely be merged, you can use locking mechanisms of subversion. There is a subversion book you can download. (just do a net search on "subversion book"). It can explain it better than me ;)


> **hambone79 said:**
> 2. If I check out several files from my repository and update one of them (i.e. checking out all parts of an assembly but only updating one or two parts) will subversion allow me to only check in the parts that changed? Also, if I try to check in all the files is it intelligent enough to ignore the files that didn't change?

Yes. That is the standard behaviour. You can also designate which files should be ignored be default. So you can keep cache files, thumbnail files, etc out of your repository.

> **hambone79 said:**
> 3. Can I setup subversion to dump the latest revision of all of my models to a read only directory that I can access with Pro/Engineer? This is a common practice in corporate CAD environments...the latest version of the CAD data is placed in a read only share...any files that need to be changed are checked out of the CAD management system while the remaining files are pulled from the read only share. This reduces the need to check-out/check-in things like standard hardware that is used in more than one assembly.

Sure. But this is hardly a feature of subversion. You just set up a CRON job to do an update. If you use a separate user or group for the central working copy, you can set its right to be read-only for all the draftsmen.

I do this little trick for my web server: I am the owner of the working copy, and the SGID bit of the root of the working copy is set. The group is the web server's group. Combined with the default umask (0022) this yields a directory that is read-only for the web server user, and fully editable by me. Read the chmod man page for info about the SGID bit. If you create a directory under a directory with an SGID bit, the new directory will have one also.

---

### Post by hambone79 on 2008-11-22
Thanks for the info! It looks like subversion is exactly what I'm looking for. :)

---

### Post by hambone79 on 2009-01-24
I hate to dig up an old thread, but I thought someone might find this useful. I have put together a tutorial and a script to make it possible to use Subversion for Pro/E and other CAD data. You can check out the article here:

[CAD Data Management with Subversion]("http://www.hacksawlabs.com/index.php?option=com_content&view=article&id=65:cad-data-management-with-subversion&catid=34:cad-tips&Itemid=53")

---

