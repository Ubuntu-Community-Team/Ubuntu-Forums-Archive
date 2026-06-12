---
title: "Which OpenGL version is on 20.04.1"
date: 2021-03-17
forum: Hardware
---

### Post by Bryan55 on 2021-03-17
I'm about to build a all new PC (except the SSD) as the CPU on my old one packed up.

 As the CPU I want does not have integrated graphics it will need a GPU that works out of the box with 20.04 that is now on my SSD
The card I'm looking at supports OpenGL 4.5 .   Will that be on 20.04 ?

The card I had before is listed below.

Thanks for any help.

---

### Post by CelticWarrior on 2021-03-17
Any card you can buy now new will beat a "[COLOR=#000000]ATI Radeon HD 4850 512MB" many times over.[/COLOR]

---

### Post by Yellow Pasque on 2021-03-17
If it's an AMD card, OpenGL 4.5 has been supported by the default radeonsi 3D driver for some years now (2016).
On Nvidia side, they've supported 4.5 since version 340.xx back in 2014.

> The card I'm looking at 
In future, it would help to be more specific..

---

### Post by Bryan55 on 2021-03-17
Sorry I don't seem to be making myself clear.

I have a SSD with 20.04.1 on, but have not got a working PC to boot it up. All I would like to know is what version of GL maybe on it? Is it 4.5 ??

This would then allow me to chose a GPU that can use 4.5 and give me a display.

The reason I refereed to my old GPU was I thought it might shed some light on what GL version I had.

A new development is that someone has suggested the old GPU may work on the motherboard (Asus Tuf B550-plus) I intend to get. So if I need to update the GL version I could do it with this. Then I could put in a GPU of higher spec.

---

### Post by Yellow Pasque on 2021-03-17
> All I would like to know is what version of GL maybe on it? Is it 4.5 ??

It depends on the GPU and driver. As stated, the drivers for AMD and Nvidia on 20.04 support OpenGL 4.5 (actually, they support 4.6) if the GPU supports it.
If you threw the 4850 in there, it would only support 3.3. You cannot magically upgrade your OpenGL version beyond what the GPU supports.

For open source drivers, this is a good reference (radeonsi is used for modern AMD GPU's): [https://mesamatrix.net/](https://mesamatrix.net/)

---

### Post by Bryan55 on 2021-03-19
Thanks for the reply Yellow Pasque.  Sorry for the delay on my response but I needed to research the MBD and CPU I intend to have.

What I'm not sure of is how I get a new GPU, that requires GL 4.5 , to work. The motherboard (Tuf gaming B550 plus) and the CPU (Ryzen 5 3600) do not have integrated graphics. So the GPU will need to work in order for the system to Post and maybe not even boot. In order for the GPU to work it will need to have drivers. How do I get the Ubuntu OS to provide the drivers?

---

### Post by mikewhatever on 2021-03-19
[OpenGL]("https://www.opengl.org/") isn't a program that gets installed, and then that version is "on it". Support for OpenGL comes from several different sources, such as [mesa/]("https://www.mesa3d.org/") and hardware drivers. Ubuntu does not make drivers, hardware vendors do.
Some hardware drivers are included with the Linux kernel, and are loaded on demand, if the right hardware is detected. That should have been the case with Radeon HD 4850 and Ubuntu 20.04. Some hardware drivers are not included, and those need to be installed by the user. 
There is no way to guess which graphics card you want to buy, and no way to guarantee it will just work. 
You might want to do some homework, and search for specific models with "ubuntu" as a keyword.

---

### Post by Bryan55 on 2021-03-19
> [OpenGL]("https://www.opengl.org/")[COLOR=#000000] isn't a program that gets installed, and then that version is "on it". Support for OpenGL comes from several different sources, such as [/COLOR][mesa/]("https://www.mesa3d.org/")[COLOR=#000000] and hardware drivers. Ubuntu does not make drivers, hardware vendors do.[/COLOR] 
Yes I understand Ubuntu does not make the drivers.

> [COLOR=#000000]Some hardware drivers are included with the Linux kernel, and are loaded on demand[/COLOR]
Will GL 4.5 or 4.6 be there so they can load automatically, at first boot, when a GPU that supports GL 4.5 or 4.6 is there?

> [COLOR=#000000]That should have been the case with Radeon HD 4850 and Ubuntu 20.04.[/COLOR]
When I installed the Radeon GPU it was on a MBD that had integrated graphics so I had a usable display which allowed me to install its drivers. (Propitiatory, later moved to GL) The new MBD / CPU will not post at all without a GPU and it's drivers.

> [COLOR=#000000]There is no way to guess which graphics card you want to buy, and no way to guarantee it will just work.[/COLOR]
[COLOR=#000000]You might want to do some homework, and search for specific models with "ubuntu" as a keyword.[/COLOR]
I have been specifically looking for a GPU that has been proven to work with Ubuntu and has support for OpenGL. 
However because the World has goon made at the moment with the regards to supply and price GPU's I'm unable to find one that is available. So hopping the old Radeon will give me a couple of months use to wait for the supply to get back to normal.

---

### Post by mikewhatever on 2021-03-19
As said above, OPenGL "will be there" if you choose the right card, and the hardware vendor implemented support for it. Since we are talking about an unknown model, there is no way to tell.
It is also impossible to list all the GPUs that "work with Ubuntu and has support for OpenGL". Most do, but life is too short for that.

---

### Post by Yellow Pasque on 2021-03-19
> So hoping the old Radeon will give me a couple of months use to wait for the supply to get back to normal.

It will work just fine with Ubuntu's open source radeon drivers. I wish you would have said this in your initial post instead of talking about getting a new GPU.

> What I'm not sure of is how I get a new GPU, that requires GL 4.5 , to work

That doesn't make any sense. GPU's are capable of accelerating OpenGL. They do not require it. I'm not sure where you read about OpenGL 4.5 or how you got fixated on it. Do you have some app/game that requires it?

---

### Post by Bryan55 on 2021-03-19
Thanks for your help mikewhatever.

I've always done Kernel update so GL 4.5 should be there?

I have found GPU's that do have GL 4.5 support but are out of stock or are going for way over RRP . 
It seems that some major retailers are not even renew stock. For instance Curry's in the UK have zero GPU's. Even company's that specialise in build PC are not taking any orders which would be my preferred option.

---

### Post by mikewhatever on 2021-03-19
Yep, it is not the best time to buy a new graphics card. If the old one works, it is recommended to wait, if not, get a used one.

---

### Post by Yellow Pasque on 2021-03-19
> **Bryan55 said:**
> I have found GPU's that do have GL 4.5 support

Again, you don't need an OpenGL 4.5 GPU unless you have some game/app that requires it. The RadeonHD 4850 only does OpenGL 3.3, but it will work just fine in the new mobo and with Ubuntu 20.04. No worries there.

---

### Post by Bryan55 on 2021-03-19
Thanks everyone.

Will marked this as Solved.

---

