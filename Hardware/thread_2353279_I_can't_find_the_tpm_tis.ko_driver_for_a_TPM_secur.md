---
title: "I can't find the tpm_tis.ko driver for a TPM security module (16_04 kernel)"
date: 2017-02-20
forum: Hardware
---

### Post by Fernando Acero on 2017-02-20
Hello:

I need to configure a TPM 2.0 security module under Ubuntu 16.04 LTS but I can't locate the module tpm_tis.ko into /lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/ directory.

I only can find the following modules:

/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_atmel.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_crb.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_i2c_atmel.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_i2c_infineon.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_i2c_nuvoton.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_infineon.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/tpm_nsc.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/st33zp24/tpm_st33zp24.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/st33zp24/tpm_st33zp24_i2c.ko
/lib/modules/4.4.0-62-generic/kernel/drivers/char/tpm/st33zp24/tpm_st33zp24_spi.ko
 
tpm_tis.ko  is the device driver for TCG/TCPA TPM (trusted platform module) and I need it. 

I have checked it in other kernels,  for example OpenSUSE, and I found  it.

Best regards

---

### Post by okayokayblahblah on 2017-07-05
Did you ever figure out the answer to this question - I am having the same problem

---

