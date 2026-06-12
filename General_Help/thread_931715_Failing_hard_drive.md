---
title: "Failing hard drive?"
date: 2008-09-27
forum: General Help
---

### Post by nagius on 2008-09-27
After suspecting my windows hard drive (ubuntu has it's own hd) is failing due to frequent B.S.O.D and freezes. I checked in ubuntu and I can see the files in the windows xp H.D transfer files between partitions.


Well didn't know what to make of it until I tried smartmontools utility which says:

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
Failed Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   041   041   140    Pre-fail  Always   FAILING_NOW 1265

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
					element that failed is not known.
Total time to complete Offline 
data collection: 		 (8760) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 104) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

I think this pretty much confirms that the drive is about to fail although the drive is only a few months old:mad: What do you think?

Luckily is only my windows partition but I also have my backup partition in this drive. Whats the best way to get an image of the windows partition and backup my data to a new drive? Before I lose all my dat

---

### Post by cariboo on 2008-09-27
Go to the hard drives manufacturers web site and download the diagnostic utility and run it to confirm what smartctl says. Usually you have to run the diagnostics to get an error code so that you can get an RMA for warranty replacement.

Jim

---

