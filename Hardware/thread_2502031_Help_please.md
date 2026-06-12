---
title: "Help please"
date: 2024-10-30
forum: Hardware
---

### Post by eduardo976095 on 2024-10-30
I want to activate the TPM and Secure Boot and for some reason the TPM does not detect Ubuntu properly. I have a Lenovo Thinkpad T450 and I put that distribution on it because it is the one that works best for it, but it does not finish installing properly and sometimes it also takes a while to start as if it were looking for Ubuntu. I don't know if that can be solved too.

Device Security Report
======================


Report details
  Date generated:                                  2024-10-30 14:53:25
  fwupd version:                                   1.9.24


System details
  Hardware model:                                  LENOVO 20BUS35B00
  Processor:                                       Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
  OS:                                              Ubuntu 24.04.1 LTS
  Security level:                                  HSI:0! (v1.9.24)


HSI-1 Tests
  Firmware BIOS Region:                          ! Fail (No bloqueada)
  UEFI Bootservice Variables:                      Pass (Bloqueado)
  Intel Management Engine Version:               ! Fail 
  Firmware Write Protection Lock:                  Pass (Activada)
  Platform Debugging:                              Pass (No activada)
  UEFI Secure Boot:                              ! Fail (No activada)
  Intel Management Engine Manufacturing Mode:      Pass (Bloqueado)
  BIOS Firmware Updates:                           Pass (Activada)
  Firmware Write Protection:                       Pass (No activada)
  Intel Management Engine Override:                Pass (Bloqueado)
  TPM v2.0:                                      ! Fail (No encontrada)


HSI-2 Tests
  Intel BootGuard Fuse:                            Pass (Válido)
  Intel BootGuard Verified Boot:                   Pass (Válido)
  Intel BootGuard ACM Protected:                   Pass (Válido)
  Intel BootGuard:                                 Pass (Activada)
  IOMMU Protection:                                Pass (Activada)
  BIOS Rollback Protection:                        Pass (Activada)
  Platform Debugging:                              Pass (Bloqueado)


HSI-3 Tests
  Suspend To RAM:                                ! Fail (Activada)
  Intel BootGuard Error Policy:                    Pass (Válido)
  Pre-boot DMA Protection:                       ! Fail (No activada)
  Control-flow Enforcement Technology:           ! Fail (No admitida)
  Suspend To Idle:                               ! Fail (No activada)


HSI-4 Tests
  Encrypted RAM:                                 ! Fail (No admitida)
  Supervisor Mode Access Prevention:               Pass (Activada)


Runtime Tests
  Firmware Updater Verification:                   Pass (No envenenado)
  Linux Swap:                                    ! Fail (No cifrado)
  Linux Kernel Lockdown:                         ! Fail (No activada)
  Linux Kernel Verification:                       Pass (No envenenado)


Host security events
  2024-10-30 02:18:59   Firmware BIOS Region       Fallo&#769; (Bloqueado &#8594; No bloqueada)
  2024-10-30 01:53:29   Linux Kernel Lockdown      Fallo&#769; (Activada &#8594; No activada)
  2024-10-30 01:53:29   UEFI Secure Boot           Fallo&#769; (Activada &#8594; No activada)


For information on the contents of this report, see [https://fwupd.github.io/hsi.html](https://fwupd.github.io/hsi.html)

---

### Post by yancek on 2024-10-30
Your post is confusing because you say that "because it is the one that works best" and in the same sentence you say it "it does not finish installing properly".  So do you have Ubuntu installed?  Are you referring to booting and installed system?  Or are you referring to starting the 'live' installer?  You should be able to boot and install Ubuntu with TPM enabled/disabled and with Secure Boot On or Off.  If TPM does not detect Ubuntu, what message do you see when you try to boot?

The link you posted for the software you are appearing to use for tests states on their site "[B]This specification is still in active development: it is  incomplete, subject to change, and may have errors; use this at your own  risk."  

[/B]

---

