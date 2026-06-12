---
title: "Hard Drive Performance + ext4: Advice Wanted"
date: 2015-03-08
forum: Hardware
---

### Post by peridian on 2015-03-08
Hi,

I recently performed the following commands on each of my hard drives:


[LIST]
[*]smartctl -a /dev/sdX
[*]dd if=/dev/zero of=/dev/sdX bs=4M
[*]smartctl -a /dev/sdX
[*]dd if=/dev/sdX of=/dev/null bs=4M
[*]smartctl -a /dev/sdX
[/LIST]

Not the most comprehensive test, but /dev/urandom was immensely slow (3 days per drive).  However, the output from smartctl did not indicate any errors so it's a quick enough way of testing the drives.

I was a bit puzzled by the speeds reported by the dd commands.  Given that the motherboards and cables are all SATA3, and that the dd commands are against the unformatted devices, do the below speeds make sense?

Also, given the drives in question (smartctl -i data included below), should I specify any additional options when using mkfs -t ext4 in order to better optimize the formatting?

Regards,
Rob.

```

Machine 1: All 4 drives identical type:


=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K2000
Device Model:     Hitachi HDS722020ALA330
Firmware Version: JKAOA3MA
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s


/dev/sda


Write
476932+1 records in
476931+1 records out
2000398934016 bytes (2.0 TB) copied, 19775.8 s, 101 MB/s


Read
476932+1 records in
476932+1 records out
2000398934016 bytes (2.0 TB) copied, 19732.2 s, 101 MB/s


/dev/sdb


Write
476933+0 records in
476932+0 records out
2000398934016 bytes (2.0 TB) copied, 19707.8 s, 102 MB/s


Read
476932+1 records in
476932+1 records out
2000398934016 bytes (2.0 TB) copied, 19680.1 s, 102 MB/s


/dev/sdc


Write
476933+0 records in
476932+0 records out
2000398934016 bytes (2.0 TB) copied, 19834.9 s, 101 MB/s


Read
476932+1 records in
476932+1 records out
2000398934016 bytes (2.0 TB) copied, 19351.8 s, 103 MB/s


/dev/sdd


Write
476933+0 records in
476932+0 records out
2000398934016 bytes (2.0 TB) copied, 19592.8 s, 102 MB/s


Read
476932+1 records in
476932+1 records out
2000398934016 bytes (2.0 TB) copied, 19516.2 s, 102 MB/s

```

```

Machine 2: All 4 drives the same, except where noted:


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD30EZRX-00DC0B0
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)


/dev/sda


Write
715398+0 records in
715397+0 records out
3000592982016 bytes (3.0 TB) copied, 25235 s, 119 MB/s


Read
715397+1 records in
715397+1 records out
3000592982016 bytes (3.0 TB) copied, 25212.9 s, 119 MB/s


/dev/sdb


Write
715398+0 records in
715397+0 records out
3000592982016 bytes (3.0 TB) copied, 26773.3 s, 112 MB/s


Read
715397+1 records in
715397+1 records out
3000592982016 bytes (3.0 TB) copied, 26689.8 s, 112 MB/s


/dev/sdc


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-22D8PB0


Write
715398+0 records in
715397+0 records out
3000592982016 bytes (3.0 TB) copied, 27127.2 s, 111 MB/s


Read
715397+1 records in
715397+1 records out
3000592982016 bytes (3.0 TB) copied, 27091.7 s, 111 MB/s


/dev/sdd


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00SPEB0


Write
715398+0 records in
715397+0 records out
3000592982016 bytes (3.0 TB) copied, 23444.5 s, 128 MB/s


Read
715397+1 records in
715397+1 records out
3000592982016 bytes (3.0 TB) copied, 23432.9 s, 128 MB/s

```

---

### Post by tgalati4 on 2015-03-08
Those speeds look normal.  It's difficult to get spinners above 100MB/sec, especially 7200 rpm drives.  The Western Digital drive is using a faster SATA mode so you get a little more performance 119MB/sec.  High-performance, server drives often run at 10K or 15K, but they are smaller disks with less capacity.  So you can have big storage at slow speed or small storage at fast speed.  

There are hybrid drives with SSD's built-in, so they give fast read and write speeds for certain workloads.  For data that is not accessed as frequently, it is pushed to the spinner.

You could use RAID0 to get you ~200MB/sec of throughput, which gamers tend to use, but reliability will be reduced.  Hitachi Deathstars are called that for a reason.

If you want to take advantage of SATA3 speeds, you need to use faster storage devices.  My 10K, 75GB WD Raptor drives are only 77MB/sec and they are several years old.  I'm not sure how fast the newer ones are.

Answer: [http://www.xlr8yourmac.com/IDE/SSD_vs_VelociRaptor_vs_Raptor/SSD_vs_VelociRaptor_Raptor.html](http://www.xlr8yourmac.com/IDE/SSD_vs_VelociRaptor_vs_Raptor/SSD_vs_VelociRaptor_Raptor.html) (over 100 MB/sec for older Raptors)

[http://www.tomshardware.com/reviews/velociraptor-1tb-hdd-ssd,3250.html](http://www.tomshardware.com/reviews/velociraptor-1tb-hdd-ssd,3250.html) (200 MB/sec for newer Raptors)

---

