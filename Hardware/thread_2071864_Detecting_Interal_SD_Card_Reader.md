---
title: "Detecting Interal SD Card Reader"
date: 2012-10-16
forum: Hardware
---

### Post by jeffpkamp on 2012-10-16
I have a toshiba qosmio with an internal SD card reader.  When I put an SD card in, it does not mount the card. I did lspci and I believe I see the SD card reader listed as:

07:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)

I did a few searches for answers, and it seems this is a semi-common problem.  However, the posts where they seemed to have success, I did not understand the methods.  On this post: [http://forums.opensuse.org/english/get-technical-help-here/hardware/430220-sd-card-usb-not-mounted-suse-11-2-a.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/430220-sd-card-usb-not-mounted-suse-11-2-a.html) 
the last post stated :
"
reading the bugzilla thread I found:

                                                         Looks as if there was a BIOS (ACPI?) bug                      
     
 
This rang a bell..
In order to complete the installation I had to add the "acpi=off" to kernel options.
Without this option the laptop crashed at the startup of the x server.

Reading in this forum I found that this problem may be probably solved  running the Sax tool. Indeed I managed to configure the x server while  acpi was off, I can now start with the acpi on.

EUREKA, now the SD card recognition works perfectly.
"

Not sure how to do this.  Also found:


"
                        I have found a useful workaround in another [Bug #703180]("https://bugs.launchpad.net/bugs/703180")
 Put the following in rescan.c:
 #include <stdio.h>
main(){
  FILE *outfile;
  outfile=fopen("/sys/bus/pci/rescan","w");
  if (outfile != NULL){
    fprintf(outfile,"1\n");
    fclose(outfile);
  }
  else printf("permission denied\n");
}
 then compile with:
gcc rescan.c -o rescan
sudo cp rescan /usr/local/bin
sudo chown root /usr/local/bin/rescan
sudo chmod u+s /usr/local/bin/rescan
 then in system->preferences->keyboard shortcuts, create a custom keybinding (Add). The command should point to /usr/local/bin/rescan,  and set whatever key combination you like - I used the gears button on  the top left of the keyboard, which produces 'super-L'

              
"

That was at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/969583](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/969583)

I do a bit of stuff with photo editing, so I would appreciate any help so I can get the pictures off my camera!  Thanks.

---

### Post by jeffpkamp on 2012-10-16
I ran dmesg after putting the card into my computer and got the following message:



[ 4511.346205] mmc0: ADMA error
[ 4511.346237] mmc0: error -5 whilst initialising SD card
[ 4511.708923] mmc0: ADMA error
[ 4511.708965] mmc0: error -5 whilst initialising SD card
[ 4512.068543] mmc0: ADMA error
[ 4512.068579] mmc0: error -5 whilst initialising SD card
[ 4512.428665] mmc0: ADMA error
[ 4512.428707] mmc0: error -5 whilst initialising SD card

At least it is seeing that I am putting the Card into the computer... any suggestions on getting it to initialize?

---

### Post by jeffpkamp on 2012-10-16
found the following script to work around the problem, which apparently due to ADMA seeing problems where there are none. (What ADMA is, and what problems it has I do not know, but this worked instantly, no need to restart).  Go into terminal and type the following as posted.

sudo su

cat > /etc/modprobe.d/toshiba_sd_reader.conf << EOF
# Disable ADMA to workaround a sequence of errors which looks like:
# mmc0: Unexpected interrupt 0x02000000.
# mmc0: error -110 whilst initialising SD card
# when an SD card is inserted to the card reader on a Toshiba X505
# See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043)
# or [http://ubuntuforums.org/showthread.php?t=1544350](http://ubuntuforums.org/showthread.php?t=1544350)

options sdhci debug_quirks=0x40
EOF

rmmod sdhci_pci sdhci
modprobe sdhci
modprobe sdhci_pci
update-initramfs -u

exit

Worked as soon as I typed modprobe sdhci_pci.  Hope this helps anyone else with the problem.

---

