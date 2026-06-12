---
title: "HOW TO: Change a CD/DVD read speed for drives, not supported by hdparm"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by bajun on 2007-12-12
:guitar: Hello!

Many people ask a question, how to change a CD/DVD read speed for the drives, which are not supported by "hdparm" for some reasons. This is necessary for noise reduction, which produced by the drive, during the playback of musical disks or watching a film. 
Often it occurs that the "hdparm" program has no effect on the drive. It remains a question, why, but we have a workaround. I am also the owner of the such drive (Matshita UJ-861H) and, as many other people spend too much time in the search for the answer to the question indicated. Only one place has a answer, not easy to find in net.
The workaround was tested on the UbuntuStudio Gutsy. Specification:
Laptop HP Compaq 6720s, Intel Celeron M.

SpeedControl program from Thomas Fritzsche (SpeedControl - use SET STREAMING command to set the speed of DVD-drives)

Installation:

```
wget http://noto.de/speed/speedcontrol.c
```
```
gcc -o speedcontrol speedcontrol.c
```

It is maybe necessary to move a "speedcontrol" file from your home directory to /usr/bin to use a command

Usage:

```
speedcontrol [-x speed] [device]
```

If you use a standard device name (Maybe /dev/cdrom) it is possible not to give a drive name.

On my comp it works with sudo. Sample:

```
sudo speedcontrol -x8 /dev/cdrom
```

To restore a maximal speed use a -x0 option:

```
sudo speedcontrol -x0 /dev/cdrom
```

I think, that it is very important to implement such functionality into Ubuntu distribution.

---

### Post by K.Mandla on 2007-12-20
Moved to Hardware and Laptops.

---

### Post by bajun on 2008-01-03
If [http://noto.de/speed/speedcontrol.c](http://noto.de/speed/speedcontrol.c) goes offline, this is a source code for speedcontrol

```
/*
 * SpeedControl - use SET STREAMING command to set the speed of DVD-drives
 *       
 *
 * Copyright (c) 2004	Thomas Fritzsche <tf@noto.de>
 *
 *   This program is free software; you can redistribute it and/or modify
 *   it under the terms of the GNU General Public License as published by
 *   the Free Software Foundation; either version 2 of the License, or
 *   (at your option) any later version.
 *
 *   This program is distributed in the hope that it will be useful,
 *   but WITHOUT ANY WARRANTY; without even the implied warranty of
 *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *   GNU General Public License for more details.
 *
 *   You should have received a copy of the GNU General Public License
 *   along with this program; if not, write to the Free Software
 *   Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 *
 */

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <string.h>
#include <unistd.h>
#include <sys/ioctl.h>
#include <linux/cdrom.h>

 
void dump_sense(unsigned char *cdb, struct request_sense *sense)
{
  int i;
  
  printf("Command failed: ");
    
  for (i=0; i<12; i++)
    printf("%02x ", cdb[i]);
          
    if (sense) {
      printf(" - sense: %02x.%02x.%02x\n", sense->sense_key, sense->asc,
              sense->ascq);
    } else {
      printf(", no sense\n");
    }
}

int main(int argc, char *argv[])
{
  char *device = "/dev/cdrom";
  int c,fd;
  int speed = 0;
  unsigned long rw_size;
  
  unsigned char buffer[28];
  
  struct cdrom_generic_command cgc;
  struct request_sense sense;
  extern char * optarg;

  while((c=getopt(argc,argv,"x:"))!=EOF) {
    switch(c) {
      case 'x': speed = atoi(optarg); break;
      default:
        printf("Usage: speedcontrol [-x speed] [device]");
        return -1;
    }
  }

  if (argc > optind) device = argv[optind];
  
  fd = open(device, O_RDONLY | O_NONBLOCK);
  if (fd < 0) {
    printf("Can't open device %s\n", device);
    return -1;
  }


  memset(&cgc, 0, sizeof(cgc));
  memset(&sense, 0, sizeof(sense));
  memset(&buffer, 0, sizeof(buffer));

 /* SET STREAMING command */ 
  cgc.cmd[0] = 0xb6;
 /* 28 byte parameter list length */
  cgc.cmd[10] = 28; 

  cgc.sense = &sense;
  cgc.buffer = buffer;
  cgc.buflen = sizeof(buffer);
  cgc.data_direction = CGC_DATA_WRITE;
  cgc.quiet = 1;
  
  if(speed == 0) {
/* set Restore Drive Defaults */  
    buffer[0] = 4;
  }

  buffer[8] = 0xff;
  buffer[9] = 0xff;
  buffer[10] = 0xff;
  buffer[11] = 0xff;

  rw_size = 177 * speed;

/* read size */  
  buffer[12] = (rw_size >> 24) & 0xff;
  buffer[13] = (rw_size >> 16) & 0xff;
  buffer[14] = (rw_size >>  8) & 0xff;
  buffer[15] = rw_size & 0xff;

/* read time 1 sec. */
  buffer[18] = 0x03;
  buffer[19] = 0xE8;

/* write size */
  buffer[20] = (rw_size >> 24) & 0xff;
  buffer[21] = (rw_size >> 16) & 0xff;
  buffer[22] = (rw_size >>  8) & 0xff;
  buffer[23] = rw_size & 0xff;

/* write time 1 sec. */
  buffer[26] = 0x03;
  buffer[27] = 0xE8;
 
  if (ioctl(fd, CDROM_SEND_PACKET, &cgc) != 0)       
    if (ioctl(fd, CDROM_SELECT_SPEED, speed) != 0) {
      dump_sense(cgc.cmd, cgc.sense);    
      printf("ERROR.\n");
      return -1;
    }
  printf("OK...\n");
  return 0;
}
```

---

### Post by impert on 2008-03-22
Thanks a million! 
I was getting really fed up with having to open a terminal and type eject -x4 every time I wanted to hear a little Bach.

> I think, that it is very important to implement such functionality into Ubuntu distribution.

I couldn't agree more. Let's hope it gets included in Ubuntu VERY SOON.

---

### Post by robegue on 2008-06-07
Hi,
I compiled it correctly but it has no effect, as hdparm :(

I have an LG external DVD-RW:

$ cat /proc/scsi/usb-storage/0
   Host scsi0: usb-storage
       Vendor: HLDS Inc.
      Product: Super Multi DVD Rewriter
Serial Number: P02051227154408
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

---

