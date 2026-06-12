---
title: "no mount drive for motorola v360 at ubuntu dapper"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by nandes on 2006-06-11
I've a motorola v360 mobile phone with a 256mb microSD attached. I want to view the phone files to transfer them to my ubuntu or viceversa, but when i plug the phone at usb port, nothing appears.
dmesg reports this:

> [4295272.695000] usb 3-2: USB disconnect, address 6
[4296205.943000] usb 3-2: new full speed USB device using ohci_hcd and address 7
[4296206.105000] usb 3-2: configuration #1 chosen from 2 choices
[4296206.113000] scsi5 : SCSI emulation for USB Mass Storage devices
[4296206.113000] usb-storage: device found at 7
[4296206.113000] usb-storage: waiting for device to settle before scanning
[4296211.347000] Vendor: Motorola Model: Motorola Phone Rev: 2.31
[4296211.347000] Type: Direct-Access ANSI SCSI revision: 02
[4296211.370000] SCSI device sda: 494081 512-byte hdwr sectors (253 MB)
[4296211.382000] sda: Write Protect is off
[4296211.382000] sda: Mode Sense: 0b 00 00 08
[4296211.382000] sda: assuming drive cache: write through
[4296211.434000] SCSI device sda: 494081 512-byte hdwr sectors (253 MB)
[4296211.446000] sda: Write Protect is off
[4296211.446000] sda: Mode Sense: 0b 00 00 08
[4296211.446000] sda: assuming drive cache: write through
[4296211.446000] sda: sda1
[4296211.562000] sd 5:0:0:0: Attached scsi removable disk sda
[4296211.562000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[4296211.563000] usb-storage: device scan complete
[4296212.917000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296212.917000] sda: Current: sense key: Medium Error
[4296212.917000] Additional sense: No additional sense information
[4296212.917000] end_request: I/O error, dev sda, sector 494013
[4296212.917000] printk: 5 messages suppressed.
[4296212.917000] Buffer I/O error on device sda1, logical block 493912
[4296213.124000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.124000] sda: Current: sense key: Medium Error
[4296213.124000] Additional sense: No additional sense information
[4296213.124000] end_request: I/O error, dev sda, sector 494014
[4296213.124000] Buffer I/O error on device sda1, logical block 493913
[4296213.249000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.249000] sda: Current: sense key: Medium Error
[4296213.249000] Additional sense: No additional sense information
[4296213.249000] end_request: I/O error, dev sda, sector 494015
[4296213.249000] Buffer I/O error on device sda1, logical block 493914
[4296213.371000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.371000] sda: Current: sense key: Medium Error
[4296213.371000] Additional sense: No additional sense information
[4296213.371000] end_request: I/O error, dev sda, sector 494016
[4296213.371000] Buffer I/O error on device sda1, logical block 493915
[4296213.565000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.565000] sda: Current: sense key: Medium Error
[4296213.565000] Additional sense: No additional sense information
[4296213.565000] end_request: I/O error, dev sda, sector 494017
[4296213.565000] Buffer I/O error on device sda1, logical block 493916
[4296213.690000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.690000] sda: Current: sense key: Medium Error
[4296213.690000] Additional sense: No additional sense information
[4296213.690000] end_request: I/O error, dev sda, sector 494018
[4296213.690000] Buffer I/O error on device sda1, logical block 493917
[4296213.812000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.812000] sda: Current: sense key: Medium Error
[4296213.812000] Additional sense: No additional sense information
[4296213.812000] end_request: I/O error, dev sda, sector 494019
[4296213.812000] Buffer I/O error on device sda1, logical block 493918
[4296213.932000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296213.932000] sda: Current: sense key: Medium Error
[4296213.932000] Additional sense: No additional sense information
[4296213.932000] end_request: I/O error, dev sda, sector 494020
[4296213.932000] Buffer I/O error on device sda1, logical block 493919
[4296214.133000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.133000] sda: Current: sense key: Medium Error
[4296214.134000] Additional sense: No additional sense information
[4296214.134000] end_request: I/O error, dev sda, sector 494013
[4296214.134000] Buffer I/O error on device sda1, logical block 493912
[4296214.256000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.256000] sda: Current: sense key: Medium Error
[4296214.256000] Additional sense: No additional sense information
[4296214.256000] end_request: I/O error, dev sda, sector 494014
[4296214.256000] Buffer I/O error on device sda1, logical block 493913
[4296214.376000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.376000] sda: Current: sense key: Medium Error
[4296214.376000] Additional sense: No additional sense information
[4296214.376000] end_request: I/O error, dev sda, sector 494015
[4296214.578000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.578000] sda: Current: sense key: Medium Error
[4296214.578000] Additional sense: No additional sense information
[4296214.578000] end_request: I/O error, dev sda, sector 494016
[4296214.698000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.698000] sda: Current: sense key: Medium Error
[4296214.698000] Additional sense: No additional sense information
[4296214.698000] end_request: I/O error, dev sda, sector 494017
[4296214.821000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.821000] sda: Current: sense key: Medium Error
[4296214.821000] Additional sense: No additional sense information
[4296214.821000] end_request: I/O error, dev sda, sector 494018
[4296214.947000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296214.947000] sda: Current: sense key: Medium Error
[4296214.947000] Additional sense: No additional sense information
[4296214.947000] end_request: I/O error, dev sda, sector 494019
[4296215.151000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.151000] sda: Current: sense key: Medium Error
[4296215.151000] Additional sense: No additional sense information
[4296215.151000] end_request: I/O error, dev sda, sector 494020
[4296215.282000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.282000] sda: Current: sense key: Medium Error
[4296215.282000] Additional sense: No additional sense information
[4296215.282000] end_request: I/O error, dev sda, sector 494069
[4296215.405000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.405000] sda: Current: sense key: Medium Error
[4296215.405000] Additional sense: No additional sense information
[4296215.405000] end_request: I/O error, dev sda, sector 494070
[4296215.608000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.608000] sda: Current: sense key: Medium Error
[4296215.608000] Additional sense: No additional sense information
[4296215.608000] end_request: I/O error, dev sda, sector 494071
[4296215.732000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.732000] sda: Current: sense key: Medium Error
[4296215.732000] Additional sense: No additional sense information
[4296215.732000] end_request: I/O error, dev sda, sector 494072
[4296215.852000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.852000] sda: Current: sense key: Medium Error
[4296215.852000] Additional sense: No additional sense information
[4296215.852000] end_request: I/O error, dev sda, sector 494073
[4296215.978000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296215.978000] sda: Current: sense key: Medium Error
[4296215.978000] Additional sense: No additional sense information
[4296215.978000] end_request: I/O error, dev sda, sector 494074
[4296216.186000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.186000] sda: Current: sense key: Medium Error
[4296216.186000] Additional sense: No additional sense information
[4296216.186000] end_request: I/O error, dev sda, sector 494075
[4296216.310000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.310000] sda: Current: sense key: Medium Error
[4296216.310000] Additional sense: No additional sense information
[4296216.310000] end_request: I/O error, dev sda, sector 494076
[4296216.444000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.444000] sda: Current: sense key: Medium Error
[4296216.444000] Additional sense: No additional sense information
[4296216.444000] end_request: I/O error, dev sda, sector 494069
[4296216.654000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.654000] sda: Current: sense key: Medium Error
[4296216.654000] Additional sense: No additional sense information
[4296216.654000] end_request: I/O error, dev sda, sector 494070
[4296216.775000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.775000] sda: Current: sense key: Medium Error
[4296216.775000] Additional sense: No additional sense information
[4296216.775000] end_request: I/O error, dev sda, sector 494071
[4296216.895000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296216.895000] sda: Current: sense key: Medium Error
[4296216.895000] Additional sense: No additional sense information
[4296216.895000] end_request: I/O error, dev sda, sector 494072
[4296217.018000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.018000] sda: Current: sense key: Medium Error
[4296217.018000] Additional sense: No additional sense information
[4296217.018000] end_request: I/O error, dev sda, sector 494073
[4296217.222000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.222000] sda: Current: sense key: Medium Error
[4296217.222000] Additional sense: No additional sense information
[4296217.222000] end_request: I/O error, dev sda, sector 494074
[4296217.342000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.342000] sda: Current: sense key: Medium Error
[4296217.342000] Additional sense: No additional sense information
[4296217.342000] end_request: I/O error, dev sda, sector 494075
[4296217.465000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.465000] sda: Current: sense key: Medium Error
[4296217.465000] Additional sense: No additional sense information
[4296217.465000] end_request: I/O error, dev sda, sector 494076
[4296217.677000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.677000] sda: Current: sense key: Medium Error
[4296217.677000] Additional sense: No additional sense information
[4296217.677000] end_request: I/O error, dev sda, sector 101
[4296217.799000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.799000] sda: Current: sense key: Medium Error
[4296217.799000] Additional sense: No additional sense information
[4296217.799000] end_request: I/O error, dev sda, sector 102
[4296217.922000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296217.922000] sda: Current: sense key: Medium Error
[4296217.922000] Additional sense: No additional sense information
[4296217.922000] end_request: I/O error, dev sda, sector 103
[4296217.922000] printk: 24 messages suppressed.
[4296217.922000] Buffer I/O error on device sda1, logical block 2
[4296218.125000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.125000] sda: Current: sense key: Medium Error
[4296218.125000] Additional sense: No additional sense information
[4296218.125000] end_request: I/O error, dev sda, sector 104
[4296218.245000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.245000] sda: Current: sense key: Medium Error
[4296218.245000] Additional sense: No additional sense information
[4296218.245000] end_request: I/O error, dev sda, sector 105
[4296218.366000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.366000] sda: Current: sense key: Medium Error
[4296218.366000] Additional sense: No additional sense information
[4296218.366000] end_request: I/O error, dev sda, sector 106
[4296218.486000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.486000] sda: Current: sense key: Medium Error
[4296218.486000] Additional sense: No additional sense information
[4296218.486000] end_request: I/O error, dev sda, sector 107
[4296218.694000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.694000] sda: Current: sense key: Medium Error
[4296218.694000] Additional sense: No additional sense information
[4296218.694000] end_request: I/O error, dev sda, sector 108
[4296218.828000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.828000] sda: Current: sense key: Medium Error
[4296218.828000] Additional sense: No additional sense information
[4296218.828000] end_request: I/O error, dev sda, sector 101
[4296218.948000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296218.948000] sda: Current: sense key: Medium Error
[4296218.948000] Additional sense: No additional sense information
[4296218.948000] end_request: I/O error, dev sda, sector 102
[4296219.161000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.161000] sda: Current: sense key: Medium Error
[4296219.161000] Additional sense: No additional sense information
[4296219.161000] end_request: I/O error, dev sda, sector 103
[4296219.284000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.284000] sda: Current: sense key: Medium Error
[4296219.284000] Additional sense: No additional sense information
[4296219.284000] end_request: I/O error, dev sda, sector 104
[4296219.404000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.404000] sda: Current: sense key: Medium Error
[4296219.404000] Additional sense: No additional sense information
[4296219.404000] end_request: I/O error, dev sda, sector 105
[4296219.525000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.525000] sda: Current: sense key: Medium Error
[4296219.525000] Additional sense: No additional sense information
[4296219.526000] end_request: I/O error, dev sda, sector 106
[4296219.726000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.726000] sda: Current: sense key: Medium Error
[4296219.726000] Additional sense: No additional sense information
[4296219.726000] end_request: I/O error, dev sda, sector 107
[4296219.850000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.850000] sda: Current: sense key: Medium Error
[4296219.850000] Additional sense: No additional sense information
[4296219.850000] end_request: I/O error, dev sda, sector 108
[4296219.981000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296219.981000] sda: Current: sense key: Medium Error
[4296219.981000] Additional sense: No additional sense information
[4296219.981000] end_request: I/O error, dev sda, sector 101
[4296220.188000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.188000] sda: Current: sense key: Medium Error
[4296220.188000] Additional sense: No additional sense information
[4296220.188000] end_request: I/O error, dev sda, sector 102
[4296220.308000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.308000] sda: Current: sense key: Medium Error
[4296220.308000] Additional sense: No additional sense information
[4296220.308000] end_request: I/O error, dev sda, sector 103
[4296220.431000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.431000] sda: Current: sense key: Medium Error
[4296220.431000] Additional sense: No additional sense information
[4296220.431000] end_request: I/O error, dev sda, sector 104
[4296220.551000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.551000] sda: Current: sense key: Medium Error
[4296220.551000] Additional sense: No additional sense information
[4296220.551000] end_request: I/O error, dev sda, sector 105
[4296220.762000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.762000] sda: Current: sense key: Medium Error
[4296220.762000] Additional sense: No additional sense information
[4296220.762000] end_request: I/O error, dev sda, sector 106
[4296220.887000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296220.887000] sda: Current: sense key: Medium Error
[4296220.887000] Additional sense: No additional sense information
[4296220.887000] end_request: I/O error, dev sda, sector 107
[4296221.007000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.007000] sda: Current: sense key: Medium Error
[4296221.007000] Additional sense: No additional sense information
[4296221.007000] end_request: I/O error, dev sda, sector 108
[4296221.221000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.221000] sda: Current: sense key: Medium Error
[4296221.221000] Additional sense: No additional sense information
[4296221.221000] end_request: I/O error, dev sda, sector 101
[4296221.356000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.356000] sda: Current: sense key: Medium Error
[4296221.356000] Additional sense: No additional sense information
[4296221.356000] end_request: I/O error, dev sda, sector 102
[4296221.587000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.587000] sda: Current: sense key: Medium Error
[4296221.587000] Additional sense: No additional sense information
[4296221.587000] end_request: I/O error, dev sda, sector 103
[4296221.795000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.795000] sda: Current: sense key: Medium Error
[4296221.795000] Additional sense: No additional sense information
[4296221.795000] end_request: I/O error, dev sda, sector 104
[4296221.917000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296221.917000] sda: Current: sense key: Medium Error
[4296221.917000] Additional sense: No additional sense information
[4296221.917000] end_request: I/O error, dev sda, sector 105
[4296222.037000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.037000] sda: Current: sense key: Medium Error
[4296222.037000] Additional sense: No additional sense information
[4296222.037000] end_request: I/O error, dev sda, sector 106
[4296222.244000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.244000] sda: Current: sense key: Medium Error
[4296222.244000] Additional sense: No additional sense information
[4296222.244000] end_request: I/O error, dev sda, sector 107
[4296222.367000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.367000] sda: Current: sense key: Medium Error
[4296222.367000] Additional sense: No additional sense information
[4296222.367000] end_request: I/O error, dev sda, sector 108
[4296222.487000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.487000] sda: Current: sense key: Medium Error
[4296222.487000] Additional sense: No additional sense information
[4296222.487000] end_request: I/O error, dev sda, sector 109
[4296222.688000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.688000] sda: Current: sense key: Medium Error
[4296222.688000] Additional sense: No additional sense information
[4296222.688000] end_request: I/O error, dev sda, sector 110
[4296222.812000] sd 5:0:0:0: SCSI error: return code = 0x8000002
[4296222.812000] sda: Current: sense key: Medium Error
[4296222.812000] Additional sense: No additional sense information
[4296222.812000] end_request: I/O error, dev sda, sector 111
nandes@ubuntu6:~$
I reported the bug at [https://launchpad.net/distros/ubuntu/+bug/49345]("https://launchpad.net/distros/ubuntu/+bug/49345")

---

### Post by Robertk on 2008-03-31
I have exactly the same problem. It has only been a problem since Gutsy Gibbon, in Feisty it worked fine.

---

