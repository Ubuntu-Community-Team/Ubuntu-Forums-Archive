---
title: "Printer - Canon MX310"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by StonePiano on 2007-10-04
Has anyone been able to get a Canon MX310 printer to work with Linux?

It's a all-in-one fax, scanner, printer, copier.  When I run the New Printer wizard, Ubuntu detects it an suggests two options:
Canon MX310 series FAX (Canon MX310 series FAX USB #2)
Canon MX310 series (Canon MX310 series USB #1)

... the wizard then suggests the Canon model MultiPASS C2500 with a BJ driver.

However, when I print a test page, the printer just throws a blank page.

Thanks for any help.
Kind regards,
StonePiano

---

### Post by GJRick on 2007-12-13
I have had this same problem. Canon tells me to come here, and I can't seem to find out what driver might emulate well enough to use it for this Canon MX-310

Thanks for your help.

---

### Post by gibbons on 2008-01-13
I am using the latest Ubuntu release and my canon MX310 works well. I am using the Canon PIXMA MP150 - CUPS+Gutenprint v5.0.1 Simplified drivers.

---

### Post by bpedigo on 2008-01-22
> **gibbons said:**
> I am using the latest Ubuntu release and my canon MX310 works well. I am using the Canon PIXMA MP150 - CUPS+Gutenprint v5.0.1 Simplified drivers.

Do those drivers also work for the scanner? I can't get the scanner to work using Ubuntu 7.10.

---

### Post by nicolos on 2008-03-22
Hi,

As the maintainer of the Sane pixma library, I can propose you to test the latest Sane Pixma library with the PIXMA MX310.

If anyone could give a try with the latest libsane-pixma library 0.14.4 (or with latest Sane-CVS if you can compile it) and test MX310 scanning in flatbed mode or ADF, both should be supported.

The libsane-pixma is available from the blog (see in the signature), as long as explanations on how to install it with Sane, [[COLOR="Blue"]in this post[/COLOR]]("http://mp610.blogspot.com/2007/11/new-sane-scanner-driver-for-canon-mp610.html")

Sane-CVS is available from the [COLOR="Navy"][[COLOR="Blue"]sane-project page[/COLOR]]("http://www.sane-project.org/source.html") [/COLOR]

Let me know in any case, success or fail, so that we can include the MX310 into the Sane library.

---

### Post by nurulc on 2008-04-25
The MX310 worked rather well using the suggestion made earlier - use the MP150 settings. But the color is significantly off particularly for RED. The color i get is a light brown and quite a way off from red. The green and blue look fine at least from a casual visual inspection. Is there a way to adjust the colors.

---

### Post by nicolos on 2008-04-25
MX310 Being a recent model, did you try to use the Canon printer drivers for MP520 or MP610 ? 

They are available from the site [http://www.canon-asia.com]("http://www.canon-asia.com"), in the Support & Download section, and are available as .deb packages. 

Don't know what will be the result, but worth a try ...

> **nurulc said:**
> The MX310 worked rather well using the suggestion made earlier - use the MP150 settings. But the color is significantly off particularly for RED. The color i get is a light brown and quite a way off from red. The green and blue look fine at least from a casual visual inspection. Is there a way to adjust the colors.

---

