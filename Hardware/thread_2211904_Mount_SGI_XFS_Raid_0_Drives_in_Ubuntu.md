---
title: "Mount SGI XFS Raid 0 Drives in Ubuntu"
date: 2014-03-18
forum: Hardware
---

### Post by phillip_croxford on 2014-03-18
Hi

I'm in a bit of a predicament. I have a buffalo Link station Duo Nas Drive. the Nas drive its self has gone but im sure the data on the disks are fine.
i have plugged the 2 disks into a windows machine using a Sata to USB converter and ran a program called "UFS Explorer Raid Recovery" software.
I then built the raid 0 up and i can safely see all my data.

but I'm not prepared to pay the £100 licence when i know Linux can nativley read XFS

is there a way i can mount the two disks in a raid 0 configuration and read the data from the config? 
my main aim is to take the data from these 2 disks and to transfer the data on to my backup server.

Please bear in mind I'm limited with my Linux command line knowledge. 

any help would be appreciated

Thanks

---

### Post by lukeiamyourfather on 2014-03-18
Yes, Linux can natively read XFS. The NAS probably used mdadm for the RAID. Sounds like a LaCie NAS that I recovered a few weeks back. Below are the commands that I used, the hashed lines are comments. Run the commands one at a time.

```

# Install packages for XFS support
sudo apt-get install xfsprogs

# Install mdadm for software RAID support
sudo apt-get install mdadm

# Tell mdadm to look for existing arrays
sudo mdadm --assemble --scan

# Create a folder to mount to
sudo mkdir /nas

# Mount the filesystem
sudo mount /dev/md4 /nas

```

Note the number after the array is the partition. So /dev/md4 was what I used on my LaCie NAS but it might be a different partition on your NAS (e.g /dev/md2, /dev/md5, etc.).

---

