---
title: "Blackmagic vs Kernel 4.10"
date: 2017-04-22
forum: Hardware
---

### Post by OmnipotentEntity on 2017-04-22
Hi there,

I had some trouble getting Blackmagic drivers installed under Linux Kernel 4.10 and I figured I'd document it here such that other people don't have to go through this process.

The Problem

Attempting to install Blackmagic driver v10.8.6a2 gives an error during DKMS compilation and the log file contains the following error:

```
/var/lib/dkms/blackmagic/10.8.6a3/build/blackmagic_lib.c: In function 'dl_get_user_pages':
/var/lib/dkms/blackmagic/10.8.6a3/build/blackmagic_lib.c:669:10: error: too few arguments to function 'get_user_pages_remote'
    ret = get_user_pages_remote(current_task, current_task->mm, (unsigned long)ptr & PAGE_MASK, *nr_pages, write ? FOLL_WRITE : 0, pages, NULL);
          ^~~~~~~~~~~~~~~~~~~~~
```

The Cause

The API to get_user_pages_remote changed kernel version 4.10 due to a feature being added.  You can read more about this here: [https://github.com/torvalds/linux/commit/5b56d49fc31dbb0487e14ead790fc81ca9fb2c99](https://github.com/torvalds/linux/commit/5b56d49fc31dbb0487e14ead790fc81ca9fb2c99)

The Solution

The source code is included in the package under:

Blackmagic_Desktop_Video_Linux_10.8.6a2/other/x86_64/desktopvideo-10.8.6a2-x86_64.tar.gz

Untar this to find two files that use this function:

desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-10.8.6a2/blackmagic_lib.c
desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-io-10.8.6a2/bm_mm.c

Apply this patch to blackmagic_lib.c:

```
--- a/desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-10.8.6a2/blackmagic_lib.c	2017-04-04 00:54:02.000000000 -0400
+++ b/desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-10.8.6a2/blackmagic_lib.c	2017-04-22 14:14:32.055688065 -0400
@@ -662,7 +662,12 @@
 		write = 0;

 	down_read(&current_task->mm->mmap_sem);
-#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 9, 0)
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 10, 0)
+		if (current_task == current)
+			ret = get_user_pages((unsigned long)ptr & PAGE_MASK, *nr_pages, write ? FOLL_WRITE : 0, pages, NULL);
+		else
+			ret = get_user_pages_remote(current_task, current_task->mm, (unsigned long)ptr & PAGE_MASK, *nr_pages, write ? FOLL_WRITE : 0, pages, NULL, NULL);
+#elif LINUX_VERSION_CODE >= KERNEL_VERSION(4, 9, 0)
 		if (current_task == current)
 			ret = get_user_pages((unsigned long)ptr & PAGE_MASK, *nr_pages, write ? FOLL_WRITE : 0, pages, NULL);
```

And this patch to bm_mm.c

```
--- a/desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-io-10.8.6a2/bm_mm.c	2017-04-04 00:54:02.000000000 -0400
+++ b/desktopvideo-10.8.6a2-x86_64/usr/src/blackmagic-io-10.8.6a2/bm_mm.c	2017-04-22 14:37:57.395802405 -0400
@@ -103,7 +103,12 @@
 		return false;

 	down_read(&task->mm->mmap_sem);
-#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 9, 0)
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 10, 0)
+		if (task == current)
+			ret = get_user_pages((unsigned long)address & PAGE_MASK, umem->length, write ? FOLL_WRITE : 0, umem->pages, NULL);
+		else
+			ret = get_user_pages_remote(task, task->mm, (unsigned long)address & PAGE_MASK, umem->length, write ? FOLL_WRITE : 0, umem->pages, NULL, NULL);
+#elif LINUX_VERSION_CODE >= KERNEL_VERSION(4, 9, 0)
 		if (task == current)
 			ret = get_user_pages((unsigned long)address & PAGE_MASK, umem->length, write ? FOLL_WRITE : 0, umem->pages, NULL);
 		else
```

Then recreate the tar file and repackage the .deb using the debian tar file.

Or you can use this finely crafted deb file, standard disclaimers apply, I've only ever tested it on my computer, if it makes your computer catch on fire, well, you should have been more careful, I'm not even sending it over SSL, total amateur hour here.

Also you're downloading a driver from some random person on the internet.  What's wrong with you?

The sha256 checksum is: 450f7d86d2d3a2a760bb5729fd6fafc803de6079d06608e6fd047ee912b28cae  desktopvideo_10.8.6a2_amd64.deb

The file is located at [fixed.space/files/desktopvideo_10.8.6a2_amd64.deb](http://fixed.space/files/desktopvideo_10.8.6a2_amd64.deb)

---

### Post by jakarr on 2017-05-31
> **OmnipotentEntity said:**
> 
Or you can use this finely crafted deb file, standard disclaimers apply, I've only ever tested it on my computer, if it makes your computer catch on fire, well, you should have been more careful, I'm not even sending it over SSL, total amateur hour here.

Also you're downloading a driver from some random person on the internet.  What's wrong with you?

The sha256 checksum is: 450f7d86d2d3a2a760bb5729fd6fafc803de6079d06608e6fd047ee912b28cae  desktopvideo_10.8.6a2_amd64.deb


The irony here is that the official files from Blackmagic are sent over regular HTTP. And I couldn't find checksums either. Searching for them brought me here.

---

