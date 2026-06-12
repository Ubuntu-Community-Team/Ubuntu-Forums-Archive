---
title: "trouble installing ispconfig -mcpu-"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Applebear786 on 2006-01-04
i get the following error when installing ispconfig. i let it continue doing this for about 15 minutes...

what's going on?

message below.

thanks in advance for your help.

`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o p5_pbe.o p5_pbe.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o p5_pbev2.o p5_pbev2.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o p8_pkey.o p8_pkey.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o asn_moid.o asn_moid.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
ar r ../../libcrypto.a a_object.o a_bitstr.o a_utctm.o a_gentm.o a_time.o a_int.o a_octet.o a_print.o a_type.o a_set.o a_dup.o a_d2i_fp.o a_i2d_fp.o a_enum.o a_utf8.o a_sign.o a_digest.o a_verify.o a_mbstr.o a_strex.o x_algor.o x_val.o x_pubkey.o x_sig.o x_req.o x_attrib.o x_bignum.o x_long.o x_name.o x_x509.o x_x509a.o x_crl.o x_info.o x_spki.o nsseq.o d2i_pu.o d2i_pr.o i2d_pu.o i2d_pr.o t_req.o t_x509.o t_x509a.o t_crl.o t_pkey.o t_spki.o t_bitst.o tasn_new.o tasn_fre.o tasn_enc.o tasn_dec.o tasn_utl.o tasn_typ.o f_int.o f_string.o n_pkey.o f_enum.o a_hdr.o x_pkey.o a_bool.o x_exten.o asn1_gen.o asn1_par.o asn1_lib.o asn1_err.o a_meth.o a_bytes.o a_strnid.o evp_asn1.o asn_pack.o p5_pbe.o p5_pbev2.o p8_pkey.o asn_moid.o
/usr/bin/ranlib ../../libcrypto.a || echo Never mind.
make[2]: Leaving directory `/tmp/install_ispconfig/compile_aps/openssl-0.9.8/crypto/asn1'
making all in crypto/pem...
make[2]: Entering directory `/tmp/install_ispconfig/compile_aps/openssl-0.9.8/crypto/pem'
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o pem_sign.o pem_sign.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o pem_seal.o pem_seal.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
gcc -I.. -I../.. -I../../include -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -mcpu=pentium -DL_ENDIAN -DTERMIO -O3 -fomit-frame-pointer -Wall -DOPENSSL_BN_ASM_PART_WORDS -DOPENSSL_IA32_SSE2 -DSHA1_ASM -DMD5_ASM -DRMD160_ASM -DAES_ASM -c -o pem_info.o pem_info.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.

---

### Post by pieboy314 on 2006-01-18
me too!!

what up, nobody has any ideas? :confused:

---

### Post by pieboy314 on 2006-01-19
it seems fairly obvious to me that the problems is...

> `-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.

and this sends the install into an error loop, but I can't change the install procedure... isn't everyone who tries to setup IspConfig running into this?

I was thinking about trying an older release of IspConfig... ???

---

### Post by pieboy314 on 2006-01-21
well, I ended up bailing on this after many attempts and angles to fix this, and I reinstalled.

But, incase you are picking up this thread because you are having the same problem, it was suggested to me that this is not an error, it is a warning and this is not a loop it just appears to be and if you let it run long enough it will install.

I let it loop for about 15 oe 20 minutes but I was told I could have waited it out.

just fyi...

---

### Post by livinginx on 2007-01-17
Yeah, I waited it out, installed just fine.

---

