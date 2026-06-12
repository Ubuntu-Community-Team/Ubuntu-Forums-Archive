---
title: "Patching ata_piix.c to improve intel sata controller performance"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by roger99 on 2007-04-22
Hi,

I have a Dell Inspiron 6400 laptop, running feisty, which is working ok but i have noticed that the disk access is not as fast as it should be.

Hdparm tells me I am getting an average of 26-30mb per sec.  With no dma activated. Which i think is a bit slow.

I have found [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=342931&highlight=Intel+ICH7+82801GBM%2FGHMA") thread, which states that I may get an improvement by activating DMA by patching ata_piix.c.

I have the following info as the patch

```
-- linux-2.6.17/drivers/scsi/ata_piix.c	2006-09-03 16:37:16.000000000 +0300
+++ linux-2.6.17-new/drivers/scsi/ata_piix.c	2006-09-03 16:39:14.000000000 +0300
@@ -326,15 +326,15 @@
 static const struct piix_map_db ich6m_map_db = {
 	.mask = 0x3,
 	.port_enable = 0x5,
 	.present_shift = 4,
 	.map = {
 		/* PM   PS   SM   SS       MAP */
 		{  P0,  P2,  RV,  RV }, /* 00b */
-		{  RV,  RV,  RV,  RV },
+		{ IDE, IDE,  P1,  P3 }, /* 01b */
 		{  P0,  P2, IDE, IDE }, /* 10b */
 		{  RV,  RV,  RV,  RV },
 	},
 };
 
 static const struct piix_map_db ich8_map_db = {
 	.mask = 0x3,
```

I have this in the existing ata_piix.c on my disk

```
static const struct piix_map_db ich6m_map_db = {
	.mask = 0x3,
	.port_enable = 0x5,

	/* Map 01b isn't specified in the doc but some notebooks use
	 * it anyway.  MAP 01b have been spotted on both ICH6M and
	 * ICH7M.
	 */
	.map = {
		/* PM   PS   SM   SS       MAP */
		{  P0,  P2,  RV,  RV }, /* 00b */
		{ IDE, IDE,  P1,  P3 }, /* 01b */
		{  P0,  P2, IDE, IDE }, /* 10b */
		{  RV,  RV,  RV,  RV },
	},
};

static const struct piix_map_db ich8_map_db = {
	.mask = 0x3,
	.port_enable = 0x3,
	.map = {
		/* PM   PS   SM   SS       MAP */
		{  P0,  P2,  P1,  P3 }, /* 00b (hardwired when in AHCI) */
		{  RV,  RV,  RV,  RV },
		{  IDE,  IDE,  NA,  NA }, /* 10b (IDE mode) */
		{  RV,  RV,  RV,  RV },
	},
};
```

Now this is where the questions start rising !?! :rolleyes:

I am presuming that the lines in the patch with a plus and minus sign would be the line to remove and replace?

In which case does this mean that this patch has been applied allready and something else is the cause of my sloooow hard disk!!

If i do need to apply this patch, errrrrrr, exactly how do I go about it.  Is the driver like a module which I can just recompile or do I need to compile into the kernel?  Can I do that into the ubuntu kernel? or do I need to compile myself a completly new kernel using sources from kernel.org

Sorry for all the questions, and thanks for all the answers in advance :)

---

### Post by Roddles on 2007-12-19
Was wondering if you managed to get a response to this - Is the ata_piix module already patched in ubuntu gutsy?

If so - my SATA performance is still terrible :(

Rod.

---

### Post by Roddles on 2007-12-23
Just an update

From what i have googled on this so far, the patch is already applied in ubuntu.

My performance problems were actually caused by a BIOS setting in my dell laptop. If you are using a Dell XPS M1710, set the Disk Accoustics performance option to BYPASS and do not have it set to Performance. This got my SATA speeds back up to where they should be.

---

