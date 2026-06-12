---
title: "I need help with hardware. I am Brazilian."
date: 2023-08-25
forum: Hardware
---

### Post by pedberdog on 2023-08-25
I'm having problems with the hardware. Here is the diagnosis:

where has Passou (bloqueado): Passed (Blocked)
where has ! Falhou (Inválido): ! Failed (Invalid)
where has ! Falhou (Desabilitado): ! Failed (Disabled)
where has ! Falhou (Habilitado): ! Failed (Enabled)
where has ! Falhou (Não localizado): ! Failed (Not found)
where has ! Falhou (Comprometido): ! Failed (Committed)
where has ! Falhou (Não encriptado): ! Failed (Not Encrypted)
where has ! Falhou (Sem suporte): ! Failed (Unsupported)

Relatório de segurança do dispositivo
======================


Detalhes do relatório
  Data em que foi gerado:                          2023-08-25 19:21:49
  Versão do fwupd:                                 1.8.12


System details
  Modelo do hardware:                              Acer Nitro AN517-54
  Processador:                                     11th Gen Intel(R) Core(TM) i7-11800H @ 2.30GHz
  SO:                                              Ubuntu 23.04
  Nível de segurança:                              HSI:0! (v1.8.12)


HSI-1 Testes
  TPM v2.0:                                        Passou (Encontrado)
  UEFI Platform Key:                               Passou (Válido)
  MEI Key Manifest:                                Passou (Válido)
  Firmware BIOS Region:                            Passou (Bloqueado)
  Intel Management Engine Version:               ! Falhou (Inválido)
  Firmware Write Protection Lock:                  Passou (Habilitado)
  Platform Debugging:                              Passou (Desabilitado)
  Intel Management Engine Manufacturing Mode:      Passou (Bloqueado)
  UEFI Secure Boot:                                Passou (Habilitado)
  Firmware Write Protection:                       Passou (Desabilitado)
  TPM Platform Configuration:                      Passou (Válido)
  Intel Management Engine Override:                Passou (Bloqueado)


HSI-2 Testes
  Intel BootGuard Fuse:                            Passou (Válido)
  Intel BootGuard Verified Boot:                 ! Falhou (Inválido)
  Intel BootGuard ACM Protected:                 ! Falhou (Inválido)
  Intel BootGuard:                                 Passou (Habilitado)
  IOMMU Protection:                              ! Falhou (Não localizado)
  TPM Reconstruction:                              Passou (Válido)
  Platform Debugging:                              Passou (Bloqueado)


HSI-3 Testes
  Suspend To RAM:                                ! Falhou (Habilitado)
  Intel BootGuard Error Policy:                  ! Falhou (Inválido)
  Pre-boot DMA Protection:                         Passou (Habilitado)
  Intel CET:                                       Passou (Habilitado)
  Suspend To Idle:                               ! Falhou (Desabilitado)


HSI-4 Testes
  Encrypted RAM:                                 ! Falhou (Sem suporte)
  Intel SMAP:                                      Passou (Habilitado)


Testes de tempo de execução
  Linux Kernel Verification:                     ! Falhou (Comprometido)
  Firmware Updater Verification:                   Passou (Não comprometido)
  Linux Swap:                                    ! Falhou (Não encriptado)
  Linux Kernel Lockdown:                           Passou (Habilitado)
  Intel CET:                                       Passou (Suportado)


Eventos de segurança do host


Para obter informações sobre o conteúdo deste relatório, consulte [https://fwupd.github.io/hsi.html](https://fwupd.github.io/hsi.html)

---

