---
title: "OpenGL version hardware support"
date: 2009-11-15
forum: Hardware
---

### Post by Rastanarcharismarx on 2009-11-15
Hello community,

A little intro and situation description:
I'm am planning on building a new rig. It will be the first one I'll be building by myself and I'll also be doing my first steps into linux as well. I am planning on putting a GeForce 8400GS on it (it is cheap, has linux support and works pretty well on MS Windows as well), and the videocard manufacturer (Club 3D) offers a 8400GS with OpenGL 3.0 support on it (on their most recent revision) according to their [specs sheet]("http://www.club3d.nl/products/pdfs/CGNX-GS842L.pdf"). However the vendor I'm planning to buy from has a previous shipment with version 2.1 on them, which is still neat since most manufacturers ship with 2.0, but not as neat as getting 3.0 for the same price.
The Question:
Does it really matter which version of OpenGL is supported by my graphics card?

---

### Post by Melcar on 2009-11-15
If it's DX10 capable hardware it can use OpenGL3.x (last time I heard).

---

### Post by Yellow Pasque on 2009-11-15
[http://developer.nvidia.com/object/opengl_3_driver.html](http://developer.nvidia.com/object/opengl_3_driver.html)

---

### Post by Rastanarcharismarx on 2009-11-15
> **Melcar said:**
> If it's DX10 capable hardware it can use OpenGL3.x (last time I heard).

Coming to think of it... before DirectX 8.1, DirectX updates usually didn't require hardware updates for proper hardware rendering (my >10 years old win 98se computer still passes all dxdiag tests including direct3D except for the 8.1 Direct3D specific ones).
So I guess that 3.x will most likely work regardless of the revision of the card (8400GS is on the market for quite some time anyway and club 3D seems to be the only one mentioning 3.0 support - so the "Rev. 1.0 Mar-2009" on the spec sheet probably refers to a revision of the specs and not of the hardware)

> **Temüjin said:**
> [http://developer.nvidia.com/object/opengl_3_driver.html](http://developer.nvidia.com/object/opengl_3_driver.html)

Thanks for the link.
The [faq on the link]("http://developer.nvidia.com/object/opengl_3_driver.html#faq") mentions that OpenGL 3.0, 3.1 and 3.2 is supported on G80 and newer chips and thus will work on
- GeForce 8000 series or higher; Geforce G100, GT120, 130, 220, GTS 150, GTS 250, GeForce GTX 260 and higher, any ION based products.
- Quadro FX 370, 570, 1700, 3700, 4600, 4700x2, 4800, 5600, 5800, Quadro VX200, Quadro CX
Just to be sure I did some further research and discovered that the 8400GS has a G86-core (which later got replaced by a G98? confusing) which got lauched later than G80 so it should be openGL 3.0/3.1/3.2 compatible anyway.
whoever isn't about which version of OpenGL is supported by his nVidia graphics card can check [this comparison of NVIDIA GPU's on wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_NVIDIA_Graphics_Processing_Units").

---

