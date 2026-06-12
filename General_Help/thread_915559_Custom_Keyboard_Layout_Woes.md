---
title: "Custom Keyboard Layout Woes"
date: 2008-09-10
forum: General Help
---

### Post by mhopgood on 2008-09-10
I'm a long time reader, first time poster (an LTRFTP!) and I was hoping to get some help.

Being a Dvorak user and a student of Attic Greek, I've been trying to combine my two loves with a Greek Dvorak keyboard layout. Unable to find one on Google, I decided to make my own. I modified the standard Greek keyboard, and while the system doesn't give me error messages (anymore), It still types as though it were in the QWERTY Greek layout.

I'm completely boggled as to how this can be, and have checked and rechecked the xkb.list and xkb.xml files; I've also rebooted the X-Server several times out of desperation.

I'll my layout gr_dv layout here to see if anyone can give me some much appreciated help!

// $XKeyboardConfig: xkeyboard-config/symbols/gr_dv, 2008-09-09 21:49:32  $

default
xkb_symbols "basic" {

    include "gr(bare)"

    name[Group1] = "Greece Dvorak";

    key <TLDE> { [        grave,  asciitilde ] }; // ` ~
    key <AE01> { [            1,      exclam ] }; // 1 !
    key <AE02> { [            2,          at ] }; // 2 @
    key <AE03> { [            3,  numbersign ] }; // 3 #
    key <AE04> { [            4,      dollar ] }; // 4 $
    key <AE05> { [            5,     percent ] }; // 5 %
    key <AE06> { [            6, asciicircum ] }; // 6 ^
    key <AE07> { [            7,   ampersand ] }; // 7 &
    key <AE08> { [            8,    asterisk ] }; // 8 *
    key <AE09> { [            9,   parenleft ] }; // 9 (
    key <AE10> { [            0,  parenright ] }; // 0 )
    key <AE11> { [  bracketleft,   braceleft ] }; // [ {
    key <AE12> { [ bracketright,  braceright ] }; // [ {

    key <AD11> { [        slash,    question ] }; // / ?
    key <AD12> { [        equal,        plus ] }; // = +

    key <AC11> { [   apostrophe,    quotedbl ] }; // ' "

    key <AB08> { [ Greek_finalsmallsigma,    Greek_SIGMA ] }; // &#962; &#931;
    key <AB09> { [           Greek_omega,    Greek_OMEGA ] }; // &#969; &#937;
    key <AB10> { [            Greek_zeta,     Greek_ZETA ] }; // &#950; &#918;
    key <BKSL> { [    backslash,         bar ] }; // \ |

    include "kpdl(comma)"
};

xkb_symbols "bare" {

    key <AD01> { [            apostrophe,       quotedbl ] }; // ' "
    key <AD02> { [                 comma,           less ] }; // , <
    key <AD03> { [                period,        greater ] }; // . >
    key <AD04> { [              Greek_pi,       Greek_PI ] }; // &#960; &#928;
    key <AD05> { [           Greek_theta,    Greek_THETA ] }; // &#952; &#920;
    key <AD06> { [             Greek_phi,      Greek_PHI ] }; // &#966; &#934;
    key <AD07> { [           Greek_gamma,    Greek_GAMMA ] }; // &#947; &#915;
    key <AD08> { [             Greek_psi,      Greek_PSI ] }; // &#968; &#936;
    key <AD09> { [             Greek_rho,      Greek_RHO ] }; // &#961; &#929;
    key <AD10> { [           Greek_lamda,    Greek_LAMDA ] }; // &#955; &#923;

    key <AC01> { [           Greek_alpha,    Greek_ALPHA ] }; // &#945; &#913;
    key <AC02> { [         Greek_omicron,  Greek_OMICRON ] }; // &#959; &#927;
    key <AC03> { [         Greek_epsilon,  Greek_EPSILON ] }; // &#949; &#917;
    key <AC04> { [         Greek_upsilon,  Greek_UPSILON ] }; // &#965; &#933;
    key <AC05> { [            Greek_iota,     Greek_IOTA ] }; // &#953; &#921;
    key <AC06> { [           Greek_delta,    Greek_DELTA ] }; // &#948; &#916;
    key <AC07> { [             Greek_eta,      Greek_ETA ] }; // &#951; &#919;
    key <AC08> { [             Greek_tau,      Greek_TAU ] }; // &#964; &#932;
    key <AC09> { [              Greek_nu,       Greek_NU ] }; // &#957; &#925;
    key <AC10> { [           Greek_sigma,    Greek_SIGMA ] }; // &#963; &#931;

    key <AB01> { [             semicolon,          colon ] }; // ; :
    key <AB02> { [            apostrophe,       quotedbl ] }; // ' "
    key <AB03> { [             Greek_chi,      Greek_CHI ] }; // &#967; &#935;
    key <AB04> { [              Greek_xi,       Greek_XI ] }; // &#958; &#926;
    key <AB05> { [           Greek_kappa,    Greek_KAPPA ] }; // &#954; &#922;
    key <AB06> { [            Greek_beta,     Greek_BETA ] }; // &#946; &#914;
    key <AB07> { [              Greek_mu,       Greek_MU ] }; // &#956; &#924;

    key <LSGT> { [         guillemotleft, guillemotright ] }; // « »
};

---

### Post by simosx on 2008-09-11
First of all, there is a keyboard layout editor for XKB, at
[http://code.google.com/p/keyboardlayouteditor/](http://code.google.com/p/keyboardlayouteditor/)

I loaded this layout and I noticed that it is the same with the current default Greek layout.

I do not know how the dvorak layout looks like for Greek.

I also noticed that the layout support modern Greek only; when you work with Attic Greek, do you use the whole set of accents and tones?

In Ubuntu 8.10 there will be full support for Greek Polytonic; it will work out of the box.

There is some effort to modify the existing default Greek layout so that it is possible to type polytonic as well,
[http://bugs.freedesktop.org/show_bug.cgi?id=17459](http://bugs.freedesktop.org/show_bug.cgi?id=17459)
This might make it in Ubuntu 8.10.

---

### Post by fooledbyprimes on 2010-01-31
I am also learning Attic (Koine) Greek.  I am in a bad position because I am using Dvorak (English) layout and not Qwerty.    I really want to make a copy of the standard polytonic greek layout and then edit it so that the keys are mapped to a Dvorak layout.  This is the same idea that the above user tried to do.   I wonder if he/she was successful???   I am a programmer so I can edit text files with a lot of patience.  But before I start I wanted to get an expert opinion on if Dvorak with Polytonic Greek is possible.   Can I do this?  I REALLY hope I can.   Simosx, thanks for your help and advice!!  

Also,  How easy is it to copy the Polytonic Greek layout and rename the new copy?  Is it just one text file or is it more complicated???


Thank you so very much!

---

### Post by simosx on 2010-02-03
> **fooledbyprimes said:**
> I am also learning Attic (Koine) Greek.  I am in a bad position because I am using Dvorak (English) layout and not Qwerty.    I really want to make a copy of the standard polytonic greek layout and then edit it so that the keys are mapped to a Dvorak layout.  This is the same idea that the above user tried to do.   I wonder if he/she was successful???   I am a programmer so I can edit text files with a lot of patience.  But before I start I wanted to get an expert opinion on if Dvorak with Polytonic Greek is possible.   Can I do this?  I REALLY hope I can.   Simosx, thanks for your help and advice!!  

Also,  How easy is it to copy the Polytonic Greek layout and rename the new copy?  Is it just one text file or is it more complicated???


You can definitely make a Greek Polytonic Dvorak layout.

Some tips: 
1. You would probably start with a Greek Dvorak layout, such as
[https://unstable.nl/andreas/el_dv.html](https://unstable.nl/andreas/el_dv.html)
2. The next step is to place the extra Greek Polytonic dead keys. These are about 4-5 extra characters to the existing layout.
3. You can use the 'Greece Polytonic' section at /usr/share/X11/xkb/symbols/gr and place there the Dvorak layout.
4. You can use a text editor for these changes.

If the layout is complete, similarly to the default Greek layout, ask to have it added upstream.

---

