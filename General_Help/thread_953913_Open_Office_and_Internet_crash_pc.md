---
title: "Open Office and Internet crash pc"
date: 2008-10-20
forum: General Help
---

### Post by xenos90 on 2008-10-20
When I try to run OpenOffice and Firefox or Pidgin together, my computer invariably crashes. I have no idea why.

---

### Post by larnal29 on 2008-11-12
Hello!
I have somewhat the same problem.
I run Intrepid and decided to install OO 3. I decided that as OO 2.4 would crash all the time and ask for recovery of...nothing...so I wiped it out and installed OO3. The problem is that I still have occasional crashes and especially when I run firefox with OO. I end up recovering my documents and I'm sccared I could definitely corrupt them.

Did anybody have the same crash issue?

---

### Post by larnal29 on 2008-11-12
here is the crash report that I get:
Does anybody know where could be the problem?

word and excel docs

================

Was browsing the web and oo was in the background when it suddenly crashed. Fourth time today....

================

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE errormail:errormail PUBLIC "-//OpenOffice.org//DTD ErrorMail 1.0//EN" "errormail.dtd">
<errormail:errormail xmlns:errormail="http://openoffice.org/2002/errormail" usertype="">
<reportmail:mail xmlns:reportmail="http://openoffice.org/2002/reportmail" version="1.1" feedback="false" email="">
<reportmail:title></reportmail:title>
<reportmail:attachment name="description.txt" media-type="text/plain" class="UserComment"/>
<reportmail:attachment name="stack.txt" media-type="text/plain" class="pstack output"/>
</reportmail:mail>
<officeinfo:officeinfo xmlns:officeinfo="http://openoffice.org/2002/officeinfo" build="300m9(Build:9358)" platform="unxlngi6.pro" language="" exceptiontype="11" product="OpenOffice.org 3.0" procpath="/opt/openoffice.org3/program/"/>
<systeminfo:systeminfo xmlns:systeminfo="http://openoffice.org/2002/systeminfo">
<systeminfo:System name="Linux" version="#1 SMP Tue Nov 4 19:33:20 UTC 2008" build="2.6.27-7-generic" locale="C"/>
<systeminfo:CPU type="i686"/>
</systeminfo:systeminfo>
<errormail:Stack type="Linux">
<errormail:StackInfo pos="0" ip="0xb7e7dc80" rel="0x1fc80" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="1" ip="0xb7e7e564" rel="0x20564" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="2" ip="0xb8034400" rel="0x400" name="" ordinal="__kernel_sigreturn+0x0"/>
<errormail:StackInfo pos="3" ip="0xb4aa0d87" rel="0x8d87" name="libfontconfig.so.1" path="/usr/lib/" ordinal="FcConfigSubstitute+0x27"/>
<errormail:StackInfo pos="4" ip="0xb632c7e4" rel="0x3b7e4" name="libpspli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZNK3psp16PrintFontManager10SubstituteERKN3rtl8OUStringERS2_RKNS1_7OStringENS_6italic4typeENS_6weight4typeENS_5width4typeENS_5pitch4typeE+0x172"/>
<errormail:StackInfo pos="5" ip="0xb4c12cde" rel="0x33cde" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="6" ip="0xb4c12d97" rel="0x33d97" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="7" ip="0xb69b469e" rel="0x11d69e" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZNK15ImplDevFontList14ImplFindByFontER18ImplFontSelectDatabP26ImplDirectFontSubstitution+0x33c"/>
<errormail:StackInfo pos="8" ip="0xb69b56e9" rel="0x11e6e9" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="9" ip="0xb69b5c4e" rel="0x11ec4e" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="10" ip="0xb69b5e53" rel="0x11ee53" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="11" ip="0xb69b681a" rel="0x11f81a" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZNK12OutputDevice13GetTextHeightEv+0x16"/>
<errormail:StackInfo pos="12" ip="0xb6ac33ee" rel="0x22c3ee" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN9StatusBar11DataChangedERK16DataChangedEvent+0x76"/>
<errormail:StackInfo pos="13" ip="0xb0b3e542" rel="0x1cd542" name="libfwkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="14" ip="0xb6ae77b9" rel="0x2507b9" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN6Window14UpdateSettingsERK11AllSettingsh+0x233"/>
<errormail:StackInfo pos="15" ip="0xb6ae7800" rel="0x250800" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN6Window14UpdateSettingsERK11AllSettingsh+0x27a"/>
<errormail:StackInfo pos="16" ip="0xb6926352" rel="0x8f352" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11Application11SetSettingsERK11AllSettings+0x1ba"/>
<errormail:StackInfo pos="17" ip="0xb6afbcd5" rel="0x264cd5" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="18" ip="0xb4c2cdee" rel="0x4ddee" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN10SalDisplay21DispatchInternalEventEv+0xb6"/>
<errormail:StackInfo pos="19" ip="0xb522a975" rel="0x13975" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="20" ip="0xb522aadf" rel="0x13adf" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="21" ip="0xb4c8e7c1" rel="0x377c1" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="22" ip="0xb4c906f8" rel="0x396f8" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_dispatch+0x1e8"/>
<errormail:StackInfo pos="23" ip="0xb4c93da3" rel="0x3cda3" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="24" ip="0xb4c93f61" rel="0x3cf61" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_iteration+0x71"/>
<errormail:StackInfo pos="25" ip="0xb522aa32" rel="0x13a32" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="26" ip="0xb4c348fa" rel="0x558fa" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14X11SalInstance5YieldEbb+0x2c"/>
<errormail:StackInfo pos="27" ip="0xb6925bdf" rel="0x8ebdf" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11Application5YieldEb+0x5f"/>
<errormail:StackInfo pos="28" ip="0xb6925c31" rel="0x8ec31" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11Application7ExecuteEv+0x2f"/>
<errormail:StackInfo pos="29" ip="0xb7e1bf8e" rel="0x22f8e" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="30" ip="0xb692b5e0" rel="0x945e0" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="31" ip="0xb692b76b" rel="0x9476b" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_Z6SVMainv+0x29"/>
<errormail:StackInfo pos="32" ip="0xb7e441ab" rel="0x4b1ab" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="soffice_main+0xdb"/>
<errormail:StackInfo pos="33" ip="0x8048dea" rel="0xdea" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="main+0x16"/>
<errormail:StackInfo pos="34" ip="0xb798c685" rel="0x16685" name="libc.so.6" path="/lib/tls/i686/cmov/" ordinal="__libc_start_main+0xe5"/>
<errormail:StackInfo pos="35" ip="0x8048d41" rel="0xd41" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="__gxx_personality_v0+0x31"/>
</errormail:Stack>
<errormail:Checksums type="MD5">
<errormail:Checksum sum="0x194687215DD7D8289267F3041665AC61" bytes="1790624" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x194687215DD7D8289267F3041665AC61" bytes="1790624" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x5DB58D88F678B4D5D72CF7DCE34B4FE4" bytes="179024" file="libfontconfig.so.1"/>
<errormail:Checksum sum="0xC232C93CC5332DA74DB49B2F379A2657" bytes="917376" file="libpspli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x3D3B026C8B1695BD37370EBCE64ABCB7" bytes="2838272" file="libfwkli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x297B924EAD4820E62D15CFD230973948" bytes="743852" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x297B924EAD4820E62D15CFD230973948" bytes="743852" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x297B924EAD4820E62D15CFD230973948" bytes="743852" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x297B924EAD4820E62D15CFD230973948" bytes="743852" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xAC7B2AC6E18BB0BA3B25A6D06FB051D7" bytes="7472" file="soffice.bin"/>
<errormail:Checksum sum="0xD9BE1CB9E983EEED00917BEF86949363" bytes="1425800" file="libc.so.6"/>
<errormail:Checksum sum="0xAC7B2AC6E18BB0BA3B25A6D06FB051D7" bytes="7472" file="soffice.bin"/>
</errormail:Checksums>
</errormail:errormail>

---

### Post by larnal29 on 2008-11-12
up :)

---

