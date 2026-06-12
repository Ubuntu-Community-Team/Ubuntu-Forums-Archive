---
title: "EAC 0.99 PreBeta 4 and Wine issue"
date: 2008-08-23
forum: General Help
---

### Post by steelblue77 on 2008-08-23
Hello,

I know this is an ongoing problem with EAC under Wine.  It seems like something new breaks everything.  I'm running Kubuntu 8.04 x386, with Wine 1.1.3 and EAC 0.99 PreBeta 4.  I think it might be a kernel issue.  My kernel is 2.6.24.21.

The hell of it is, EAC can grab the disc info, but freezes on gap detection and anything cdrom related beyond the initial info grab.  I have Win XP set in winecfg and my dvd drive is recognized properly as cdrom0 in the drives tab with the right type selected.

If I switch to Native interface in the EAC settings tab, the program won't even recognize the disc.

I executed EAC in command line and returned this:

fixme:ntdll:NtSetInformationToken 0x3c 4 0x61166988 44
fixme:ntdll:NtSetInformationToken 0x3c 6 0x6dfa30 4
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:advapi:ImpersonateLoggedOnUser (0xa4)
fixme:advapi:ImpersonateLoggedOnUser (0xc8 )
fixme:advapi:ImpersonateLoggedOnUser (0xa4)
fixme:advapi:ImpersonateLoggedOnUser (0xa4)
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg3: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg4: Permission denied
fixme:ntdll:NtSetInformationToken 0x3c 4 0x61166988 44
fixme:ntdll:NtSetInformationToken 0x3c 6 0x6dfa30 4
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:advapi:ImpersonateLoggedOnUser (0xa4)
fixme:advapi:ImpersonateLoggedOnUser (0xc8 )
fixme:advapi:ImpersonateLoggedOnUser (0xa4)
fixme:advapi:ImpersonateLoggedOnUser (0xa4)

Looks like a permissions issue (?).  I really want to get EAC working again under Wine.  Any help would be greatly appreciated.

---

### Post by Mazeppa262 on 2008-08-25
The same thing happens to me, although I got it to detect gaps with detection method "B". When I try to rip it hangs and I have to force quit.

---

### Post by steelblue77 on 2008-08-29
Yea, I was able to get the gap detection to work as well, now.  But, then everything freezes if I continue with the rip.

---

