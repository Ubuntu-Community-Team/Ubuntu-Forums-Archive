---
title: "Support for Intel NM10 chipset"
date: 2010-06-24
forum: Hardware
---

### Post by pytheas22 on 2010-06-24
I'm considering purchasing a Mini from Dell's refurbished outlet.  The models I'm interested in have graphics chipsets described as "Intel NM10 Express."  Does anyone know what that actually is?  Is it supported by the normal "intel" video driver like all of Intel's 8xx and 9xx chipsets?

I know that some Dell netbooks ship with "Intel 500 GMA" graphics cards, which don't actually have an Intel chipset at all (apparently it's a chip that Intel bought from another company) and are reportedly a big hassle to get working with Ubuntu, because there's no open-source driver.

Any information regarding the compatibility of the NM10 Express cards would be greatly appreciated before I make a purchase.

---

### Post by AltomineUK on 2010-07-09
Is it an Atom N450?.... cos they have both GPU and CPU on a single chip

---

### Post by cascade9 on 2010-07-09
From what I've seen, the NM10 chipset works under linux just fine. 

[http://www.linuxtech.net/features/intel_atom_pineview_motherboards_overview.html](http://www.linuxtech.net/features/intel_atom_pineview_motherboards_overview.html)

---

### Post by pytheas22 on 2010-07-10
Thanks, that's helpful.  I didn't realize the GPU and CPU were combined into a single chip, but that makes sense.  I suppose Linux doesn't care where the GPU is as long it has a chipset that Linux recognizes.

In any case, I already purchased a Dell Mini with i945 graphics and it works well.

---

### Post by Remiii on 2010-10-28
Hello,

I want to know if the following configuration is supported by GNU/Linux Ubuntu: Motherboard Gigabyte GA-D525TUD (eg [http://www.gigabyte.com/products/product-page.aspx?pid=3549#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3549#ov)) with Intel D525 and Intel ATOM NM10.
Thank you in advance for your answers.

Kind regards,
Remiii

---

### Post by pytheas22 on 2010-10-28
> 
I want to know if the following configuration is supported by GNU/Linux Ubuntu: Motherboard Gigabyte GA-D525TUD (eg [http://www.gigabyte.com/products/pro...px?pid=3549#ov](http://www.gigabyte.com/products/pro...px?pid=3549#ov)) with Intel D525 and Intel ATOM NM10.
Thank you in advance for your answers.


I would never make absolute promises about hardware support without being able to test it first, but everything there looks like it should work fine.  They don't tell you exactly what the audio chipset is, just that it's Intel-based, but you can be pretty certain that should work.  The Realtek RTL8111E ethernet should work out-of-the-box, or in a worst case you can download and compile the driver from Realtek's site.

Otherwise, it all looks good to me.  You might want to google the names of some of the components along with the words "linux" or "ubuntu" just to be extra safe.

---

### Post by Remiii on 2010-10-29
> **pytheas22 said:**
> I would never make absolute promises about hardware support without being able to test it first, but everything there looks like it should work fine.  They don't tell you exactly what the audio chipset is, just that it's Intel-based, but you can be pretty certain that should work.  The Realtek RTL8111E ethernet should work out-of-the-box, or in a worst case you can download and compile the driver from Realtek's site.

Otherwise, it all looks good to me.  You might want to google the names of some of the components along with the words "linux" or "ubuntu" just to be extra safe.

Thank you for your reply. I'll try and I'll let a comment on this forum. Sincerly. Remiii

---

