---
title: "Ubuntu 9 how to install my ati drivers"
date: 2010-03-22
forum: Hardware
---

### Post by invictusss on 2010-03-22
Hellol im on ubuntu in last week,but have a problem - how to install my ati and motherboard drivers .. my ati is Radeion HD 5450 Tank u!

---

### Post by Dantevus on 2010-03-22
ATI Proprietary drivers should be able to be accessed through System-Administration-Hardware Drivers. If not then you should be able to get a Linux version from the ATI website.

---

### Post by invictusss on 2010-03-22
I downalod  "ati-driver-installer-10-2-x86.x86_64.run" from the ati web site for linux ati 5xxx series .. but don't k'now hot to install this one ... please help me.Im amateur in this situation(sorry for my bad english) Tank u!

---

### Post by Dantevus on 2010-03-22
It's no problem at all. Open a terminal and input these commands.

```
cd /home/(yourusername)/(wherever you downloaded it to)
```

```
sudo apt-get update
```

```
sudo sh ./ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic
```

```
sudo dpkg -i *.deb
```

Let me know how it works out for you. I'll be checking in from time to time until I get confirmation that you have it working :)

---

### Post by invictusss on 2010-03-22
tank u! is happening!Tank u very mach!

---

### Post by Dantevus on 2010-03-22
My pleasure

---

### Post by invictusss on 2010-03-22
> **Dantevus said:**
> My pleasure

The ati driver is now installed but when i restart the pc have a problem: update you system,back up configuration and i give the back up configuration option because on every other make my monitor very colored ... when i log on to X start the aty catalysator control centre but write Not Ati grafics is installed,or te ATI driver is not functioning properly,Please Install the ATI driver apporiate for you ATI hardware,or configure using aticonfig... where can i find aticonfig in the folder ATI do't have this kind of file.When i start firefox open page with this one:

<PROFILES>
<!-- =========================== -->
<!-- Workstation Applications    -->
<!-- =========================== -->
<!-- 3ds max -->
&#8722;
<_3dsmax>
<OpenGLCaps>0x00008040</OpenGLCaps>
<OpenGLCapsEx>0x20000000</OpenGLCapsEx>
<CrossFireCaps>0x00000010</CrossFireCaps>
</_3dsmax>
<!-- ABAQUS -->
&#8722;
<abq661>
<PROFILENAME>ProfileAbaqus</PROFILENAME>
</abq661>
&#8722;
<ABQvwrK>
<PROFILENAME>ProfileAbaqus</PROFILENAME>
</ABQvwrK>
&#8722;
<ABQcaeK>
<PROFILENAME>ProfileAbaqus</PROFILENAME>
</ABQcaeK>
<!-- AutoCAD -->
&#8722;
<acad>
<OpenGLCaps>0x00D00000</OpenGLCaps>
</acad>
<!-- Accelrys Discovery Studio -->
&#8722;
<discoverystudio>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio>
&#8722;
<discoverystudio17>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio17>
&#8722;
<discoverystudio17-bin>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio17-bin>
&#8722;
<discoverystudio20>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio20>
&#8722;
<discoverystudio20-bin>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio20-bin>
&#8722;
<discoverystudio21>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio21>
&#8722;
<discoverystudio21-bin>
<OpenGLCaps>0x00000040</OpenGLCaps>
</discoverystudio21-bin>
&#8722;
<discoverystudio22>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio22>
&#8722;
<discoverystudio22-bin>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio22-bin>
&#8722;
<discoverystudio25>
<PROFILENAME>ProfileDiscoveryStudio</PROFILENAME>
</discoverystudio25>
&#8722;
<discoverystudio25-bin>
<OpenGLCaps>0x00000040</OpenGLCaps>
</discoverystudio25-bin>
<!-- Adobe After Effects -->
&#8722;
<afterfx>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</afterfx>
<!-- Altair HyperWorks -->
&#8722;
<hmopengl>
<PROFILENAME>ProfileHyperWorks</PROFILENAME>
</hmopengl>
<!-- Altair HyperWorks Version 9 -->
&#8722;
<hc90_wxp>
<PROFILENAME>ProfileHyperWorks</PROFILENAME>
</hc90_wxp>
<!-- Altair HyperWorks Version 10 -->
&#8722;
<hc10_wxp>
<PROFILENAME>ProfileHyperWorks</PROFILENAME>
</hc10_wxp>
<!-- Altair HyperWorks Version 10 -->
&#8722;
<hc100_wxp>
<PROFILENAME>ProfileHyperWorks</PROFILENAME>
</hc100_wxp>
<!-- ArcGIS -->
&#8722;
<arcglobe>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</arcglobe>
<!-- Autodesk Inventor -->
&#8722;
<inventor>
<PROFILENAME>ProfileInventor</PROFILENAME>
</inventor>
&#8722;
<perforation>
<PROFILENAME>ProfileInventor</PROFILENAME>
</perforation>
&#8722;
<scooch>
<PROFILENAME>ProfileInventor</PROFILENAME>
</scooch>
<!-- Autodesk ShowCase -->
&#8722;
<showcasepro>
<OpenGLCaps>0x01000000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</showcasepro>
<!-- Autodesk Revit -->
&#8722;
<revit>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</revit>
<!-- Autodesk VIZ -->
&#8722;
<_3dsviz>
<OpenGLCaps>0x00008040</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</_3dsviz>
<!-- AxioVision -->
&#8722;
<axiovs40>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</axiovs40>
<!-- CATIA -->
&#8722;
<cnext>
<PROFILENAME>ProfileCatia</PROFILENAME>
</cnext>
&#8722;
<catstart>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catstart>
&#8722;
<catsysdemon>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catsysdemon>
&#8722;
<catgtsperformances>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catgtsperformances>
&#8722;
<ve0perfo>
<PROFILENAME>ProfileCatia</PROFILENAME>
</ve0perfo>
&#8722;
<dmu>
<PROFILENAME>ProfileCatia</PROFILENAME>
</dmu>
&#8722;
<enovia>
<PROFILENAME>ProfileCatia</PROFILENAME>
</enovia>
&#8722;
<delmia>
<PROFILENAME>ProfileCatia</PROFILENAME>
</delmia>
&#8722;
<delmia_lcm>
<PROFILENAME>ProfileCatia</PROFILENAME>
</delmia_lcm>
&#8722;
<gw0srvcx>
<PROFILENAME>ProfileCatia</PROFILENAME>
</gw0srvcx>
&#8722;
<plm3dnav>
<PROFILENAME>ProfileCatia</PROFILENAME>
</plm3dnav>
&#8722;
<catgts2d>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catgts2d>
&#8722;
<catgts3d>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catgts3d>
&#8722;
<catgtstextures>
<PROFILENAME>ProfileCatia</PROFILENAME>
</catgtstextures>
&#8722;
<enovweb3d>
<PROFILENAME>ProfileCatia</PROFILENAME>
</enovweb3d>
&#8722;
<_3dliveplayer>
<PROFILENAME>ProfileCatia</PROFILENAME>
</_3dliveplayer>
&#8722;
<_3dxmlplayer>
<PROFILENAME>ProfileCatia</PROFILENAME>
</_3dxmlplayer>
<!-- Cinebench -->
&#8722;
<COMPANY_maxon_computer_gmbh>
<PROFILENAME>ProfileCinebench</PROFILENAME>
</COMPANY_maxon_computer_gmbh>
<!-- dissolve -->
&#8722;
<dissolve>
<CrossFireCaps>0x00000010</CrossFireCaps>
</dissolve>
<!-- Ensight -->
&#8722;
<ens82cl>
<PROFILENAME>ProfileEnsight</PROFILENAME>
</ens82cl>
&#8722;
<ens90cl>
<PROFILENAME>ProfileEnsight</PROFILENAME>
</ens90cl>
<!-- EliteCAD -->
&#8722;
<cad>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</cad>
<!-- Fgl_glxgears -->
&#8722;
<fgl_glxgears>
<CrossFireCaps>0x00000010</CrossFireCaps>
</fgl_glxgears>
<!-- Fluent -->
&#8722;
<fluent>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</fluent>
<!-- FreeForm Modeling Plus -->
&#8722;
<freeformmodelingplus>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</freeformmodelingplus>
<!-- Glxgears -->
&#8722;
<glxgears>
<CrossFireCaps>0x00000010</CrossFireCaps>
</glxgears>
<!-- Houdini -->
&#8722;
<houdini>
<PROFILENAME>ProfileHoudini</PROFILENAME>
</houdini>
&#8722;
<hmaster>
<PROFILENAME>ProfileHoudini</PROFILENAME>
</hmaster>
<!-- ICEM Surf -->
&#8722;
<uim>
<OpenGLCaps>0x00400425</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</uim>
<!-- I-DEAS NX -->
&#8722;
<ideamn>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</ideamn>
&#8722;
<geomod>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</geomod>
&#8722;
<suptab>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</suptab>
&#8722;
<tdas>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</tdas>
&#8722;
<genmach>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</genmach>
&#8722;
<idm>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</idm>
&#8722;
<archive>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</archive>
&#8722;
<mds>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</mds>
&#8722;
<pcm>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</pcm>
&#8722;
<wsgtst>
<PROFILENAME>ProfileIdeasNx</PROFILENAME>
</wsgtst>
<!-- IronCAD -->
&#8722;
<ironcad>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ironcad>
<!-- LightWave 3D -->
&#8722;
<lightwav>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</lightwav>
<!-- Maya -->
&#8722;
<fcheck>
<OpenGLCaps>0x00400000</OpenGLCaps>
<OpenGLCapsEx>0x00000020</OpenGLCapsEx>
</fcheck>
&#8722;
<maya>
<OpenGLCaps>0x00400000</OpenGLCaps>
<OpenGLCapsEx2>0x00000001</OpenGLCapsEx2>
<ContextMain>0x00000006</ContextMain>
</maya>
<!-- Microstation -->
&#8722;
<teatime2>
<PROFILENAME>ProfileMicrostation</PROFILENAME>
</teatime2>
&#8722;
<ustation>
<PROFILENAME>ProfileMicrostation</PROFILENAME>
</ustation>
<!-- Missler Software -->
&#8722;
<COMPANY_missler_software>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</COMPANY_missler_software>
<!-- Modo -->
&#8722;
<modo>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</modo>
<!-- MSC Patran -->
&#8722;
<patran>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</patran>
<!-- OneSpace Designer Modeling -->
&#8722;
<soliddesigner>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</soliddesigner>
<!-- Opticore Opus Realizer -->
&#8722;
<realizer>
<PROFILENAME>ProfileOpusRealizer</PROFILENAME>
</realizer>
&#8722;
<realizerbinary>
<PROFILENAME>ProfileOpusRealizer</PROFILENAME>
</realizerbinary>
<!-- Opticore Opus Studio -->
&#8722;
<opusstudio>
<PROFILENAME>ProfileOpusStudio</PROFILENAME>
</opusstudio>
&#8722;
<opusstudiobinary>
<PROFILENAME>ProfileOpusStudio</PROFILENAME>
</opusstudiobinary>
<!-- Petrel -->
&#8722;
<petrel>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</petrel>
<!-- Poser -->
&#8722;
<poser>
<OpenGLCaps>0x00000008</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</poser>
<!-- PoserPro -->
&#8722;
<poserpro>
<OpenGLCaps>0x00000008</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</poserpro>
<!-- Pro/CONCEPT -->
&#8722;
<concept>
<OpenGLCaps>0x00200000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</concept>
<!-- Pro/ENGINEER Wildfire -->
&#8722;
<xtop>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</xtop>
<!-- rs-fieldlines -->
&#8722;
<rs-fieldlines>
<OpenGLCaps>0x00008000</OpenGLCaps>
</rs-fieldlines>
<!-- SOFTIMAGE|XSI -->
&#8722;
<xsi>
&#8722;
<FILEVERSION_7>
<PROFILENAME>ProfileSoftimageXSI_7</PROFILENAME>
</FILEVERSION_7>
<PROFILENAME>ProfileSoftimageXSI</PROFILENAME>
</xsi>
&#8722;
<flip>
<PROFILENAME>ProfileSoftimageXSI</PROFILENAME>
</flip>
<!-- Solidworks -->
&#8722;
<sldworks>
<PROFILENAME>ProfileSolidWorks</PROFILENAME>
</sldworks>
&#8722;
<emodelviewer>
<PROFILENAME>ProfileSolidWorks</PROFILENAME>
</emodelviewer>
&#8722;
<swbenchmark>
<PROFILENAME>ProfileSolidWorks</PROFILENAME>
</swbenchmark>
<!-- Solid Edge -->
&#8722;
<edge>
<PROFILENAME>ProfileSolidEdge</PROFILENAME>
</edge>
&#8722;
<icnct>
<PROFILENAME>ProfileSolidEdge</PROFILENAME>
</icnct>
<!-- StudioTools -->
&#8722;
<splash>
<PROFILENAME>ProfileStudioTools</PROFILENAME>
</splash>
&#8722;
<alias>
<PROFILENAME>ProfileStudioTools</PROFILENAME>
</alias>
<!-- Gdr -->
&#8722;
<gdr>
<OpenGLCaps>0x00008800</OpenGLCaps>
</gdr>
<!-- TeamCenter Visualization -->
&#8722;
<grplayer>
<PROFILENAME>ProfileTeamCenterVis</PROFILENAME>
</grplayer>
&#8722;
<grplayer_xp32>
<PROFILENAME>ProfileTeamCenterVis</PROFILENAME>
</grplayer_xp32>
&#8722;
<grplayer_x64>
<PROFILENAME>ProfileTeamCenterVis</PROFILENAME>
</grplayer_x64>
&#8722;
<grplayer_xp64>
<PROFILENAME>ProfileTeamCenterVis</PROFILENAME>
</grplayer_xp64>
&#8722;
<visview>
<PROFILENAME>ProfileTeamCenterVis</PROFILENAME>
</visview>
<!-- Tebis -->
&#8722;
<tcad>
<PROFILENAME>ProfileTebis</PROFILENAME>
</tcad>
&#8722;
<tmess>
<PROFILENAME>ProfileTebis</PROFILENAME>
</tmess>
&#8722;
<tview>
<PROFILENAME>ProfileTebis</PROFILENAME>
</tview>
&#8722;
<tsimu>
<PROFILENAME>ProfileTebis</PROFILENAME>
</tsimu>
<!-- Unigraphics -->
&#8722;
<ugraf>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</ugraf>
&#8722;
<nxapcconfig>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</nxapcconfig>
&#8722;
<gdat_nx3_i>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx3_i>
&#8722;
<gdat_nx4_i>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx4_i>
&#8722;
<gdat_nx4_i_x64>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx4_i_x64>
&#8722;
<gdat_nx5_i>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx5_i>
&#8722;
<gdat_nx5_i_x64>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx5_i_x64>
&#8722;
<gdat_nx6_i>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx6_i>
&#8722;
<gdat_nx6_i_x64>
<PROFILENAME>ProfileUnigraphics</PROFILENAME>
</gdat_nx6_i_x64>
<!-- Vitrea 2 -->
&#8722;
<vitrea>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</vitrea>
<!-- =========================== -->
<!-- Consumer Applications       -->
<!-- =========================== -->
<!-- 3DCaptan -->
&#8722;
<_3dcaptan>
<OpenGLCaps>0x00008000</OpenGLCaps>
</_3dcaptan>
<!-- AFR-FriendlyOGL -->
&#8722;
<AFR-FriendlyOGL>
<CrossFireCaps>0x00000001</CrossFireCaps>
</AFR-FriendlyOGL>
<!-- Blender -->
&#8722;
<blender-bin>
<OpenGLCaps>0x00001000</OpenGLCaps>
</blender-bin>
<!-- Chronicles Of Riddick -->
&#8722;
<sbzengine>
<PROFILENAME>ProfileChroniclesOfRiddick</PROFILENAME>
</sbzengine>
&#8722;
<riddick>
<PROFILENAME>ProfileChroniclesOfRiddick</PROFILENAME>
</riddick>
<!-- Chronicles of Riddick - Dark Athena -->
&#8722;
<darkathena>
<CrossFireCaps>0x00000001</CrossFireCaps>
</darkathena>
<!-- DOOM3 -->
&#8722;
<doom3>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
<CrossFireCaps>0x00000001</CrossFireCaps>
</doom3>
<!-- ETQW-rthread -->
&#8722;
<etqw-rthread>
<CrossFireCaps>0x00000001</CrossFireCaps>
</etqw-rthread>
<!-- ForceSingleGPU -->
&#8722;
<ForceSingleGPU>
<CrossFireCaps>0x00000010</CrossFireCaps>
</ForceSingleGPU>
<!-- Google Earth -->
&#8722;
<googleearth>
<OpenGLCaps>0x00000000</OpenGLCaps>
<OpenGLCapsEx>0x80000000</OpenGLCapsEx>
</googleearth>
<!-- HP OpenGL Demos -->
&#8722;
<flight>
<OpenGLCapsEx2>0x00000008</OpenGLCapsEx2>
</flight>
<!-- Jedi Knight II -->
&#8722;
<jk2sp>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</jk2sp>
<!-- Nexuiz -->
&#8722;
<nexuiz-linux-686-glx>
<OpenGLCapsEx>0x00000020</OpenGLCapsEx>
</nexuiz-linux-686-glx>
&#8722;
<nexuiz-linux-x86_64-glx>
<OpenGLCapsEx>0x00000020</OpenGLCapsEx>
</nexuiz-linux-x86_64-glx>
<!-- Quake 3 -->
&#8722;
<quake3>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000020</OpenGLCapsEx>
</quake3>
<!-- Quake 4 -->
&#8722;
<quake4>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</quake4>
<!-- et -->
&#8722;
<et>
<OpenGLCapsEx>0x00000020</OpenGLCapsEx>
</et>
<!-- Return To Castle Wolfenstein -->
&#8722;
<rtcw>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</rtcw>
<!-- Unreal Tournament 2003/2004 -->
&#8722;
<ut2003-bin>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ut2003-bin>
&#8722;
<ut2004-bin>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ut2004-bin>
<!-- Win-TMP -->
&#8722;
<fwtdspg2>
<OpenGLCaps>0x00000000</OpenGLCaps>
<OpenGLCapsEx>0x80000000</OpenGLCapsEx>
</fwtdspg2>
<!-- Xorg -->
&#8722;
<xorg>
<OpenGLCaps>0x00000040</OpenGLCaps>
</xorg>
<!-- XPlane9 -->
&#8722;
<x-plane-i686>
<OpenGLCapsEx2>0x00000020</OpenGLCapsEx2>
</x-plane-i686>
<!-- =========================== -->
<!-- Shared Application Profiles -->
<!-- =========================== -->
<!-- ABAQUS -->
&#8722;
<ProfileAbaqus>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileAbaqus>
<!-- Accelrys Discovery Studio -->
&#8722;
<ProfileDiscoveryStudio>
<OpenGLCaps>0x00000000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileDiscoveryStudio>
<!-- Altair HyperWorks -->
&#8722;
<ProfileHyperWorks>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000400</OpenGLCapsEx>
</ProfileHyperWorks>
<!-- Autodesk Inventor -->
&#8722;
<ProfileInventor>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileInventor>
<!-- CATIA -->
&#8722;
<ProfileCatia>
<OpenGLCaps>0x00008014</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
<ContextMain>0x00000002</ContextMain>
</ProfileCatia>
<!-- Cinebench -->
&#8722;
<ProfileCinebench>
<OpenGLCaps>0x00008000</OpenGLCaps>
</ProfileCinebench>
<!-- Chronicles Of Riddick -->
&#8722;
<ProfileChroniclesOfRiddick>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileChroniclesOfRiddick>
<!-- Ensight -->
&#8722;
<ProfileEnsight>
<OpenGLCaps>0x10000000</OpenGLCaps>
</ProfileEnsight>
<!-- Houdini -->
&#8722;
<ProfileHoudini>
<OpenGLCaps>0x00008008</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileHoudini>
<!-- I-DEAS NX -->
&#8722;
<ProfileIdeasNx>
<OpenGLCaps>0x00088000</OpenGLCaps>
<OpenGLCapsEx>0x40000000</OpenGLCapsEx>
<OpenGLCapsEx2>0x00000008</OpenGLCapsEx2>
</ProfileIdeasNx>
<!-- Microstation -->
&#8722;
<ProfileMicrostation>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileMicrostation>
<!-- Opticore Opus Realizer -->
&#8722;
<ProfileOpusRealizer>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileOpusRealizer>
<!-- Opticore Opus Studio -->
&#8722;
<ProfileOpusStudio>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileOpusStudio>
<!-- SOFTIMAGE|XSI -->
&#8722;
<ProfileSoftimageXSI>
<OpenGLCaps>0x20008000</OpenGLCaps>
<OpenGLCapsEx>0x00000400</OpenGLCapsEx>
<ContextMain>0x00000002</ContextMain>
</ProfileSoftimageXSI>
&#8722;
<ProfileSoftimageXSI_7>
<OpenGLCaps>0x20008008</OpenGLCaps>
<OpenGLCapsEx>0x00000400</OpenGLCapsEx>
<ContextMain>0x00000002</ContextMain>
</ProfileSoftimageXSI_7>
<!-- SolidWorks -->
&#8722;
<ProfileSolidWorks>
<OpenGLCaps>0x1000d000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
<ContextMain>0x00000001</ContextMain>
</ProfileSolidWorks>
<!-- SolidEdge -->
&#8722;
<ProfileSolidEdge>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
<OpenGLCapsEx2>0x00000001</OpenGLCapsEx2>
</ProfileSolidEdge>
<!-- StudioTools -->
&#8722;
<ProfileStudioTools>
<OpenGLCaps>0x00008000</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
<OpenGLCapsEx2>0x00000040</OpenGLCapsEx2>
<CrossFireCaps>0x00000010</CrossFireCaps>
</ProfileStudioTools>
<!-- TeamCenter Visualization -->
&#8722;
<ProfileTeamCenterVis>
<OpenGLCaps>0x00008800</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileTeamCenterVis>
<!-- Tebis -->
&#8722;
<ProfileTebis>
<OpenGLCaps>0x00008200</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileTebis>
<!-- Unigraphics -->
&#8722;
<ProfileUnigraphics>
<OpenGLCaps>0x00008880</OpenGLCaps>
<OpenGLCapsEx>0x00000000</OpenGLCapsEx>
</ProfileUnigraphics>
<!-- 3DSketchup -->
&#8722;
<sketchup>
<OpenGLCaps>0x00008000</OpenGLCaps>

IS THIS A ATI CONFIG ? Tank u , and sorry for the stupid question!

---

### Post by Dantevus on 2010-03-22
I was reading back through and I gave you the wrong file name for the run command. Did you happen to catch that and change the file name under the 3rd code to the correct file name that you have? Also did you download the driver for the HD 5xxx series or just the 5xxx series?

---

### Post by invictusss on 2010-03-22
Install is okey but this problem every time when i restart or put on ubuntu is the ati is nos configured

---

### Post by Yellow Pasque on 2010-03-22
```
sudo aticonfig --initial -f
```
This link is helpful for installing: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by invictusss on 2010-03-22
bebo@bebo-desktop:~$ sudo aticonfig --intial -f
[sudo] password for bebo: 
aticonfig: No supported adapters detected
bebo@bebo-desktop:~$

---

### Post by lidex on 2010-03-25
Have a look at this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

