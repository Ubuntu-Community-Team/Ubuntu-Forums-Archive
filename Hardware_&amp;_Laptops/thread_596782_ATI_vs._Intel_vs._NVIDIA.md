---
title: "ATI vs. Intel vs. NVIDIA"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by TorchlightJay on 2007-10-29
So, I am not huge into gaming or graphic design but I do like my graphics to be good, especially for compiz and beryl. I don't care if the drivers are proprietary or open source, which graphics card is generally better, especially in Linux. Thanks

---

### Post by Rumo on 2007-10-30
If you need 3d acceleration only for compiz/beryl then every card should be fast enough, so you should focus on compatibility/easy installation.

1) intel
there is an intel open source driver which is pretty good, compiz should work flawlessly, however 3d acceleration does not work with the old i855 chipset (the desktop, not notebook version(which is i815)) - at least not in my case. i915 (notebook) and newer should work fine.

2) ati
ati's linux driver were very bad in the past. They improved and even the open-source 'ati'-driver is good enough for compiz. AMD is now making a move towards an open-source driver which you actually should care about. It should work out-of-the-box as an intel chipset (I installed a Radeon X1050 yesterday).

3) nvidia
nvidia's linux drivers were the best in the past. With compiz it's a different story, however. It works, it needs some work or it doesn't work at all. My 7300 LE is of the latter one, so that's maybe why I'm a little bit upset with nvidia atm. Only closed source drivers (at least for 3d), btw.

One of the many reasons why you should care about open-source-drivers is, that their chances of improval are much better (more people work on it).

---

### Post by cymacyma on 2007-10-30
I collected lots of information about graphic chipsets, becos I'm gonna buy a new laptop!
and here is the condensation of infos.

Intel : Very good in 2D and 3D accelation. but too old versions are unable to use. and new intel GMA called X3000 series(now released x3100, But this is actually  GMA965!) are released, but those new cards are have problems with XV, so if you buy integrated X3100 laptop and want to use compiz, you have to fix bugs manually.(x3100 and x3000 are blacklisted in compiz 0.6.0) +, some compiz effects aren't work with x3000 series well. and with bug fixing, XV maybe unable and your X will use another way to playback videos.

but(I think this expression is little odd. U guys are think so? I can't speak English very well) GMA 915 to GMA 950 work  perfectely with compiz. Linux Intel drivers are open sources and support AIGLX perfectely too.


NVIDIA : Works very good with with 'nv' open drivers in 2D. but if you want use 3D accelation and compiz, you need to use restricted driver manager. but with nvidia-glx-new, your laptops or desktop computers will not be back from suspend so you need to type correction command to fix it. (And in some laptops, there are back lights problems.)

And too old graphic cards aren't supported by restricted drivers. If you want to use 3D accelation with driver manager, you have to use Geforce 4 mx at leasts.

+, NVidia's card do not support AIGLX. NVIDIA binary driver(NVIDIA_GLX) is actually accelating OpenGL by itself. but It doesn't mean that you have to install Xgl. It works with standard X.org. So just click 'restricted driver manager', then you can use 3D accelation. 

But sometimes restricted driver managers won't work. However, there is automatic binary-driver installer called 'ENVY tools' will help you!

Too much fresh(?) graphic chipsets won't work with 2D 'nv' drivers, so If you buy FX 570m series or 8800G series(8600s are work well with nvidia-glx-new), you have to change X11, 'nv' to 'vesa' after installation with alternative CDs and you must install restricted driver to use your desktop well.


ATi: Todays, ATi offering new drivers and it works very well with 'these days' graphic cards. but ATi drivers still have some problems in suspend or hibernate. I heard that these problems aren't fixed yet, so if you buy Ati based laptops or graphic cards, you have some restriction with 'those restricted drivers'!!

And ATi drivers do not support AIGLX yet. So You have to install Xgl. Fortunatley, Ubuntu 7.10 support Xgl, so just click on syneptic manager and find Xgl. Install then reboot. and click restricted driver manager to enable 3D effects.

Sometimes restricted driver manager will not work. In this case, you have to use 'Envy tools' to install drivers in another way or install manually.

I recommend you to buy Nvidia or Intel. ATi's chipsets are little unstable I think.(I'm using ATi X1400, and It spins around me~~!!!)

---------------------------------------------------------------------------------------------------------------------------------------------------------
ps. I'm Korean. Korean have no relation with English! So there are some errors in my post maybeeeeeeeeeeeeeeeeeeeee!

---

### Post by TorchlightJay on 2007-10-30
Cool, ya I have always been big into NVIDIA and wasn't sure about Intel. I have Intel and have had NVIDIA. My luck with AMD has been rather decent. Ya installing the proprietary drivers was an added task but on a whole not too bad. Once it worked, it was great. It seems more convenient. 

The only thing I didn't like about Intel was getting 3D acceleration to work. It never seemed to work the way I could get it with NVIDIA. ATi I have always hated. Now that AMD has taken over, I hope it gets better. Oh well.

---

