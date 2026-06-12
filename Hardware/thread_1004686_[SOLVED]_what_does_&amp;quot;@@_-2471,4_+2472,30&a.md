---
title: "[SOLVED] what does &amp;quot;@@ -2471,4 +2472,30&amp;quot; mean"
date: 2008-12-07
forum: Hardware
---

### Post by inxygnuu on 2008-12-07
Hello, I was through a Linux kernel update file thing, and i saw some things that looked like this:

@@ -2471,4 +2472,30
@@ -44,6 +44,7
@@ -656,6 +656,30 @@ static int __init acpi_parse_fadt(struct acpi_table_header *table)

what do all of these things mean? I am guessing that they are the location of something, but i am not sure.

Here is all of the text: (soemone please tell me if i need to remove it)

diff --git a/Documentation/filesystems/proc.txt b/Documentation/filesystems/proc.txt
index f566ad9..23f3edc 100644
--- a/Documentation/filesystems/proc.txt
+++ b/Documentation/filesystems/proc.txt
@@ -44,6 +44,7 @@ Table of Contents
   2.14	/proc/<pid>/io - Display the IO accounting fields
   2.15	/proc/<pid>/coredump_filter - Core dump filtering settings
   2.16	/proc/<pid>/mountinfo - Information about mounts
+  2.17	/proc/sys/fs/epoll - Configuration options for the epoll interface
 
 ------------------------------------------------------------------------------
 Preface
@@ -2471,4 +2472,30 @@ For more information on mount propagation see:
 
   Documentation/filesystems/sharedsubtree.txt
 
+2.17	/proc/sys/fs/epoll - Configuration options for the epoll interface
+--------------------------------------------------------
+
+This directory contains configuration options for the epoll(7) interface.
+
+max_user_instances
+------------------
+
+This is the maximum number of epoll file descriptors that a single user can
+have open at a given time. The default value is 128, and should be enough
+for normal users.
+
+max_user_watches
+----------------
+
+Every epoll file descriptor can store a number of files to be monitored
+for event readiness. Each one of these monitored files constitutes a "watch".
+This configuration option sets the maximum number of "watches" that are
+allowed for each user.
+Each "watch" costs roughly 90 bytes on a 32bit kernel, and roughly 160 bytes
+on a 64bit one.
+The current default value for  max_user_watches  is the 1/32 of the available
+low memory, divided for the "watch" cost in bytes.
+
+
 ------------------------------------------------------------------------------
+
diff --git a/Makefile b/Makefile
index b5f52f3..54ddc77 100644
--- a/Makefile
+++ b/Makefile
@@ -1,7 +1,7 @@
 VERSION = 2
 PATCHLEVEL = 6@@ -24,7 +24,6 @@
 #include <linux/init.h>
 #include <linux/interrupt.h>
 #include <linux/console.h>
-#include <linux/kallsyms.h>
 #include <linux/bug.h>
 
 #include <asm/assembly.h>
@@ -51,7 +50,7 @@
 DEFINE_SPINLOCK(pa_dbit_lock);
 #endif
 
-void parisc_show_stack(struct task_struct *t, unsigned long *sp,
+static void parisc_show_stack(struct task_struct *task, unsigned long *sp,
 	struct pt_regs *regs);
 
 static int printbinary(char *buf, unsigned long x, int nbits)
@@ -121,18 +120,19 @@ static void print_fr(char *level, struct pt_regs *regs)
 
 void show_regs(struct pt_regs *regs)
 {
-	int i;
+	int i, user;
 	char *level;
 	unsigned long cr30, cr31;
 
-	level = user_mode(regs) ? KERN_DEBUG : KERN_CRIT;
+	user = user_mode(regs);
+	level = user ? KERN_DEBUG : KERN_CRIT;
 
 	print_gr(level, regs);
 
 	for (i = 0; i < 8; i += 4)
 		PRINTREGS(level, regs->sr, "sr", RFMT, i);
 
-	if (user_mode(regs))
+	if (user)
 		print_fr(level, regs);
 
 	cr30 = mfctl(30);

---

### Post by cariboo on 2008-12-07
I looks like you are missing some language files. Go to System-->Administration-->Language Support and make sure you have language support installed.

Jim

---

### Post by inxygnuu on 2008-12-07
no, everything is fine, i just downloaded this, and opened it using gedit.

---

### Post by inxygnuu on 2008-12-12
bumpity bump...

---

### Post by Ayuthia on 2008-12-12
It looks like you are looking at a patch.  They are usually references to line numbers to a specific file.  They are differences in the file.  The patch will either + add or - remove lines in the original file based on the information in the patch.

---

### Post by inxygnuu on 2008-12-12
> **Ayuthia said:**
> It looks like you are looking at a patch.  They are usually references to line numbers to a specific file.  They are differences in the file.  The patch will either + add or - remove lines in the original file based on the information in the patch.

Thank You! I thought it was the location of certain hardware.

Thanks!
3v4n

---

