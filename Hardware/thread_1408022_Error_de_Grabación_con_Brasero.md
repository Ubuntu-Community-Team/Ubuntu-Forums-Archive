---
title: "Error de Grabación con Brasero"
date: 2010-02-15
forum: Hardware
---

### Post by Fistandantilus on 2010-02-15
Hola a Todos!

Desde que me pase a kk estoy experimentando problemas al grabar tanto CDs como DVDs con brasero. 
Al toque de iniciar la grabación, tanto como copia de CDs como desde una iso, me tira un error y únicamente me graba la estructura de los archivos...

Estuve viendo páginas buscando una solución pero no he encontrado nada...

Si alguien me puede dar una mano se los agradecería.

Les dejo el log del error:

```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_2YS57U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_75S57U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr0
    speed=48
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /home/gera/camcordersoft.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVDRAM GH22NS50 '
BraseroWodim stdout: Revision       : 'TN01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 13032 kB/s 74x CD 9x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8468 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   253 MB        
BraseroWodim stdout: Total size:      291 MB (28:50.65) = 129799 sectors
BraseroWodim stdout: Lout start:      291 MB (28:52/49) = 129799 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11607 (97:27/18)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 18
BraseroWodim stdout: Manufacturer: Plasmon Data systems Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 230050
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in real TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  253 MB written.
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 02 0F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.004s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: The current problem looks like a buffer underrun.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: It looks like 'driveropts=burnfree' does not work for this drive.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please report.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of  253 MB written (fifo 100%) [buf  95%]   0.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1079296 bytes
BraseroWodim stdout: Writing  time:   17.869s
BraseroWodim stdout: Average write speed  97.1x.
BraseroWodim stdout: Min drive buffer fill was 95%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:   20.110s
BraseroWodim stderr: wodim: fifo had 272 puts and 18 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 7 times full, min fill was 98%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

```Y por las dudas el resultado del comando "hwinfo --cdrom" y "hdparm -iI /dev/sr0":

```

gera@gera-desktop:~$ hdparm -iI /dev/sr0

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=HL-DT-ST, FwRev=TN01, SerialNo=K1V992F2416
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

gera@gera-desktop:~$ ls -al /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 2010-02-15 20:39 /dev/sr0
gera@gera-desktop:~$ hwinfo --cdrom
28: SCSI 200.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVDRAM_GH22NS50
  Unique ID: KD9E.jqdpvH78A08
  Parent ID: 7EWs.6Ubp0dagQn0
  SysFS ID: /class/block/sr0
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:11.0/host2/target2:0:0/2:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GH22NS50"
  Vendor: "HL-DT-ST"
  Device: "DVDRAM GH22NS50"
  Revision: "TN01"
  Driver: "ahci", "sr"
  Driver Modules: "ahci"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:11.0-scsi-2:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (SATA controller)
  Drive Speed: 48
gera@gera-desktop:~$ 

```

Saludos!

PD: si requieren mas info sobre el hw avisen.

---

### Post by Tosh78 on 2010-02-17
A mi me estuvo pasando lo mismo. Como me daba fiaca ponerme a buscar e investigar soluciones, lo que hice fue instalar el Nero. Instalar software propietario no es lo que mas me gusta, pero tampoco le hago asco si lo necesito. 
De todas formas, si alguien tiene una solucion como para hacer funcionar correctamente a Brasero, mejor!

---

### Post by Fistandantilus on 2010-02-18
Solo te paso con KK como a mi, o ya te viene pasando desde versiones anteriores?

---

### Post by Tosh78 on 2010-02-18
No, solo con KK, antes me funcionaba perfecto.

---

### Post by carlosbellino on 2010-03-26
Proba viendo que conectores en tu placa esten controlados por "pata_atiixp" con este comando "[FONT=monospace]dmesg | grep scsi[0-7]"[/FONT]
____________________________________________________________________
[FONT=monospace]kaname@kaname-desktop:~$ dmesg | grep scsi[0-7][    1.274677] scsi0 : ahci
[    1.274727] scsi1 : ahci
[    1.274757] scsi2 : ahci
[    1.274785] scsi3 : ahci
[COLOR=Red][    1.275092] scsi4 : pata_atiixp
[    1.275120] scsi5 : pata_atiixp[/COLOR]
[    2.079988] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.379864] scsi6 : SCSI emulation for USB Mass Storage devices
____________________________________________________________________

en mi case son los que estan en rojo (4 y 5), luego ve en cual esta conectado tu grabador con este comando: "dmesg | grep scsi | grep GH22NS50"

[/FONT][FONT=monospace]____________________________________________________________________

kaname@kaname-desktop:~$ dmesg | grep scsi | grep GH22NS50
[    2.058836] [COLOR=Red]scsi 2[/COLOR]:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[/FONT][FONT=monospace]____________________________________________________________________
[/FONT]
[FONT=monospace][FONT=Verdana]en mi caso seria el 2.. solo resta que cambies al conector 4 o 5 de tu placa.
Espero y te funcione.. 
[/FONT][/FONT]

---

