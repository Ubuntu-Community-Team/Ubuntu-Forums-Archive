---
title: "error installing .net 2.0 in wine"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-05-14
I'm trying to get .Net 2.0 set up, but I keep getting an error and it has to close and asks if I want to send an error report and blah blah blah.  I looked at the contents of the error report but can't figure out much, can anyone help?

/home/v1nsai/.wine/drive_c/windows/temp/WLFb455.tmp
```


[05/14/09,20:11:25] ========== Logging started ==========

[05/14/09,20:11:25] =====================================

[05/14/09,20:11:25] No language specified in ini file default to OS language

[05/14/09,20:11:25] Set lang to 1033

[05/14/09,20:11:25]  Pending Reboot Table state : Logging start 

[05/14/09,20:11:25]    _________________________________________

[05/14/09,20:11:25] There are no queued up pending reboot entries.

[05/14/09,20:11:25] Logging property values

[05/14/09,20:11:25] PROPERTY	ProductName	Microsoft .NET Framework 2.0

[05/14/09,20:11:25] PROPERTY		C:\windows\temp\IXP000.TMP\netfx.msi

[05/14/09,20:11:25] PROPERTY	ProductMsi	netfx.msi

[05/14/09,20:11:25] PROPERTY	Ini Filename	C:\windows\temp\IXP000.TMP\install.ini

[05/14/09,20:11:25] PROPERTY	ProductCode	

[05/14/09,20:11:25] PROPERTY	ProductRegKey	SOFTWARE\Microsoft\NET Framework Setup\NDP\v2.0.50727

[05/14/09,20:11:25] PROPERTY	ProductRegValue	OCM

[05/14/09,20:11:25] PROPERTY	ProductRegData	

[05/14/09,20:11:25] PROPERTY	ProductSupportURL	http://go.microsoft.com/fwlink/?LinkId=45396

[05/14/09,20:11:25] PROPERTY	DefaultDirInstallToken	URTInstallPath.3643236F_FC70_11D3_A536_0090278A1BB8

[05/14/09,20:11:25] PROPERTY	Install	0

[05/14/09,20:11:25] PROPERTY	SupportWin9X	1

[05/14/09,20:11:25] PROPERTY	MinNTVersion	5.0

[05/14/09,20:11:25] PROPERTY	CheckAdminRights	1

[05/14/09,20:11:25] PROPERTY	BlockOn64Platform	1

[05/14/09,20:11:25] PROPERTY	ShowFeatureOptions	0

[05/14/09,20:11:25] PROPERTY	ShowDestinationFolder	0

[05/14/09,20:11:25] PROPERTY	LogFilePrefix	dd_netfx20

[05/14/09,20:11:25] PROPERTY	CustomTextPrefix	CustomText

[05/14/09,20:11:25] PROPERTY	MSI Log name	C:\windows\temp\dd_netfx20MSI490B.txt

[05/14/09,20:11:25] PROPERTY	Msi Command Line properties	

[05/14/09,20:11:25] PROPERTY	VerboseLog	1

[05/14/09,20:11:25] PROPERTY	RebootMode	1

[05/14/09,20:11:25] PROPERTY	UILanguage	1033

[05/14/09,20:11:25] PROPERTY	BitmapFile	C:\windows\temp\IXP000.TMP\netfx.bmp

[05/14/09,20:11:25] PROPERTY	User Canceled	0

[05/14/09,20:11:25] PROPERTY	Red	

[05/14/09,20:11:25] PROPERTY	Green	

[05/14/09,20:11:25] PROPERTY	Blue	

[05/14/09,20:11:25] PROPERTY	Current Dir	C:\windows\temp\IXP000.TMP\

[05/14/09,20:11:25] PROPERTY	Temp Dir	C:\windows\temp\

[05/14/09,20:11:25] PROPERTY	Usage Mode	0

[05/14/09,20:11:25] PROPERTY	Admin Mode	0

[05/14/09,20:11:25] PROPERTY	Maintenance Mode	

[05/14/09,20:11:25] PROPERTY	Silent Mode	0

[05/14/09,20:11:25] PROPERTY	Silent Mode Uninstall	0

[05/14/09,20:11:25] PROPERTY	WatsonSilent	0

[05/14/09,20:11:25] PROPERTY	WatsonUI	0

[05/14/09,20:11:25] PROPERTY	Silent Mode UI string	

[05/14/09,20:11:25] PROPERTY	SkipAllChecks	0

[05/14/09,20:11:25] PROPERTY	WatsonGenerateManifestOnly	

[05/14/09,20:11:25] PROPERTY	UninstallWarning	1

[05/14/09,20:11:25] PROPERTY	ControlMSIService	1

[05/14/09,20:11:25] PROPERTY	RTL Language	0

[05/14/09,20:11:25] PROPERTY	PostSetupCommandRegKey	

[05/14/09,20:11:25] PROPERTY	GlobDataINIPresent	

[05/14/09,20:11:26] Checking Windows Installer version...

[05/14/09,20:11:26] msi.dll loaded ok

[05/14/09,20:11:26] Looking for: 2.0.0

[05/14/09,20:11:26] Found: 3.1.4000

[05/14/09,20:11:26] Windows Installer version ok

[05/14/09,20:11:26] Finished Checking Windows Installer version. Return code 0

[05/14/09,20:11:26] Entering CMsiInstaller::ThreadInit

[05/14/09,20:11:26] Leaving CMsiInstaller::ThreadInit

[05/14/09,20:11:26] Checking Windows Installer version...

[05/14/09,20:11:26] msi.dll loaded ok

[05/14/09,20:11:26] Looking for: 2.0.0

[05/14/09,20:11:26] Found: 3.1.4000

[05/14/09,20:11:26] Windows Installer version ok

[05/14/09,20:11:26] Finished Checking Windows Installer version. Return code 0

[05/14/09,20:11:26] Entering  CNavigator::Start

[05/14/09,20:11:26] Running all checks

[05/14/09,20:11:26] Running system checks

[05/14/09,20:11:26] SYSTEM CHECK:	: One instance of setup running		Passed

[05/14/09,20:11:26] SYSTEM CHECK:	: Administrative rights check		Passed

[05/14/09,20:11:26] SYSTEM CHECK:	: Minimum NT Version 5.0		Passed

[05/14/09,20:11:26] SYSTEM CHECK:	: Runing on 64 bit wow check		Passed

[05/14/09,20:11:26] SYSTEM CHECK:	: OCM product installed		Passed

[05/14/09,20:11:26] Running prereq checks

[05/14/09,20:11:26] PREREQ CHECK:	: Microsoft Internet Explorer 5.01		Passed

[05/14/09,20:11:26] Checking Windows Installer version...

[05/14/09,20:11:26] msi.dll loaded ok

[05/14/09,20:11:26] Looking for: 3.0.0

[05/14/09,20:11:26] Found: 3.1.4000

[05/14/09,20:11:26] Windows Installer version ok

[05/14/09,20:11:26] Finished Checking Windows Installer version. Return code 0

[05/14/09,20:11:26] PREREQ CHECK:	: Microsoft Windows Installer 3.0		Passed

[05/14/09,20:11:26] PREREQ CHECKS:		Passed

[05/14/09,20:11:26] Running block checks

[05/14/09,20:11:26] BETA CHECK:			Passed

[05/14/09,20:11:26] Entering CNavigator::WindowCreation

[05/14/09,20:11:26] Entering CNavigator::LoadPages

[05/14/09,20:11:26] Entering CMsiInstaller::IsInstalled

[05/14/09,20:11:26] Entering CMsiInstaller::GetProductCode

[05/14/09,20:11:26] Leaving CMsiInstaller::GetProductCode

[05/14/09,20:11:26] Leaving CMsiInstaller::IsInstalled

[05/14/09,20:11:26] Created Page:	Welcome Page

[05/14/09,20:11:26] Created Page:	EULA Page

[05/14/09,20:11:26] Created Page:	Progress Page

[05/14/09,20:11:26] Created Page:	Final Page

[05/14/09,20:11:26] Leaving CNavigator::LoadPages

[05/14/09,20:11:26] Entering CMsiInstaller::RegisterUIInterfaces

[05/14/09,20:11:26] Leaving CMsiInstaller::RegisterUIInterfaces

[05/14/09,20:11:43] Entering CMsiInstaller::StartInitialization

[05/14/09,20:11:43] Entering CMsiInstaller::InitSequence

[05/14/09,20:11:43] Leaving CMsiInstaller::StartInitialization

[05/14/09,20:11:43] Entering CNavigator::Next

[05/14/09,20:11:43] Leaving CNavigator::Next

[05/14/09,20:11:46] Leaving CMsiInstaller::InitSequence

[05/14/09,20:11:49] Entering CNavigator::Next

[05/14/09,20:11:49] Entering CMsiInstaller::BeginInstall

[05/14/09,20:11:49] Entering CMsiInstaller::GetMscoreeVersionFromSystem

[05/14/09,20:11:49] Version of C:\windows\system32\mscoree.dll is 2.0.50727.42

[05/14/09,20:11:49] Leaving CMsiInstaller::GetMscoreeVersionFromSystem

[05/14/09,20:11:49] Entering CMsiInstaller::GetMscoreeVersionFromMsi

[05/14/09,20:11:49] Version of mscoree.dll in the msi package is 2.0.50727.42.

[05/14/09,20:11:49] Leaving CMsiInstaller::GetMscoreeVersionFromMsi

[05/14/09,20:11:49] MsiInstallProduct called with Command line:

[05/14/09,20:11:49] USING_EXUIH=1 REBOOT=ReallySuppress FILESINUSETEXT=""

[05/14/09,20:11:53] Entering CNavigator::Next

[05/14/09,20:11:53] Leaving CNavigator::Next

[05/14/09,20:12:01] Entering CMsiInstaller::SuppressReboot

[05/14/09,20:12:01] Leaving CMsiInstaller::SuppressReboot

```

/home/v1nsai/.wine/drive_c/windows/temp/SDBb456.tmp

```
[Setup]

ProductName=Microsoft .NET Framework 2.0

ProductMsi=netfx.msi

ProductRegKey=SOFTWARE\Microsoft\NET Framework Setup\NDP\v2.0.50727

ProductRegValue=OCM

ProductSupportURL=http://go.microsoft.com/fwlink/?LinkId=45396

DefaultDirInstallToken=URTInstallPath.3643236F_FC70_11D3_A536_0090278A1BB8

SupportWin9X=1

MinNTVersion=5.0

CheckAdminRights=1

ShowFeatureOptions=0

ShowDestinationFolder=0

LogFilePrefix=dd_netfx20

VerboseLog=1

RebootMode=1

BlockOn64Platform=1

BitmapFile=netfx.bmp

CustomTextPrefix=CustomText

UninstallWarning=1

ControlMSIService=1

UILanguage=0



[DetectDarwin]

X86=3.0

I64=3.0

A64=3.0

Win9x=2.0 

NT4=2.0

Install=0

Link=http://go.microsoft.com/fwlink/?LinkId=45724

Link9x=http://go.microsoft.com/fwlink/?LinkId=45725

LinkNT4=http://go.microsoft.com/fwlink/?LinkId=45726



[DetectIE]

X86=5.0.2919.6307

A64=5.0.2919.6307

I64=5.0.2919.6307

Link=http://www.microsoft.com/windows/ie/default.asp

VersionDisplay=5.01



[DetectNetFx]

X86=2.0.50727

A64=2.0.50727

I64=2.0.50727

Link= http://go.microsoft.com/fwlink/?linkid=27895

Lang=1033

LangDetectionNeutral=1



[BlockProductCode]

{018F3F06-CDA6-492C-9B45-3687E29B7BC6}=

{729804E1-4A5D-4B66-97CA-5626865BE22A}=

{F35A613A-40BF-4180-9560-CD9D0FF4627E}=

{FA236E6A-DCA9-49E4-BE79-794B20B848F7}=

{0EC12D3A-067D-411B-A43F-1953DD19DA81}=

{35F28AC2-84A1-4046-BAC8-1B3751E8E57E}=

{303DA0A9-20DE-4B7F-99DF-8140242D67FB}=

{205F0409-5B2C-447A-84B7-E0CE7CA5AECE}=

{DA91C487-D75B-4618-A5D3-270099253901}=

{FFC31975-87D5-4526-AD31-54BBFC72EF38}=

{8CFD49DA-70EE-4CBA-8F74-A928C95FA5B2}=

{27228463-7CA9-4CE7-8D44-49C795ED88FD}=

{5C026B05-44C7-4332-941D-943257C73944}=

{71FCEDA6-D392-4BBD-9FE4-9171E6072828}=

{B8AF9676-D4B8-41D7-BAD2-1F3125770B99}=

{A8C66385-C60F-4CD8-A597-800A6F660EEB}=

{D461412D-1C69-4A69-A169-3D122B26F0A1}=

{71A59614-172D-4F9E-B5FD-F999628CB7DE}=

{9E4C800E-7E3C-4B35-8259-09F4C414C9B9}=

{9046F10C-F5E7-4871-BED9-8288F19C70DF}=

{0422BAF9-062D-4CE9-9C07-B504EA3CDE2D}=

{CE2B90F0-CD48-4916-BD86-08232BDA5820}=

{22768A83-3A91-442F-A38F-36E5774C9EB3}=

{B887CB02-DFF5-4F55-9127-27EDFB07A6EC}=

{71F8EFBF-09AF-418D-91F1-52707CDFA274}=

{EB326804-A8D5-4191-9509-D48F8A7E9655}=

{7A1ADD0C-17F3-47B8-B033-A06E189C835D}=

{90FA11B2-3912-475C-889D-DB6507FB7058}=

{09C5808D-ED2F-4310-90EB-A16DC87B611D}=

{48FF02A1-0659-497E-B939-36E23360ECD7}=

{32F6FFF6-DF95-4344-B242-23C83DD18CC8}=

{FBEBCA12-7F0B-47EF-AE36-6E949C446418}=

{0076AC37-BD40-431F-B400-89914A2C870E}=

{BE7D6A58-3864-44F0-910C-75BC7DB91A10}=

{AFB6F35F-F660-4DD7-8882-357013A08C6C}=

{FFA6B962-263E-4CAE-8771-FCE01F89FF00}=

{7D3C3D6A-3871-4DE1-A3C1-2B397C9069AA}=

{2E093ED0-7DCD-42A4-8C63-4B45CD82E698}=

{62175B2C-10B8-4B23-A276-7E780AEA9595}=

{9E72F128-39E2-4B5F-85DF-F16C108A4B7B}=

{3125894F-D735-4C52-9765-79B9A7A0EE5E}=

{7E98B728-D0DA-4E42-8488-2BA4FD3C13CE}=

{73C7C6E4-8576-4B48-96A6-55ABBFDC8773}=

{2EA1FE0C-EBE1-4F3D-BFD8-33C585C8DABF}=

{D4A4C731-6CB8-4575-9E95-4D012FF49CD2}=

{727256A5-22F2-4A93-9DF1-1A6879C30948}=

{3E2B0BE6-AFBF-46E2-B037-E07F3B96C7F8}=

{D68819AE-539D-49B6-B58C-6D96F947BBF3}=

{908661A2-ABA7-4343-A3B3-AD72A3920A6C}=

{5296F1DD-94A5-48B9-BFED-A58E4894FF12}=

{1E1C2EE1-E9CC-444F-ABBA-A478D0042F3A}=

{BB47835E-3682-4CE5-8E6A-A811698A6517}=

{FBD12B47-5DFE-4DA4-AD4A-6CFAA1380E59}=

{44568A1C-53F6-49A5-A163-CD9ADC0F76D5}=

{5A68C92C-0946-4678-A247-19F56B31B6C8}=

{45841CBE-7212-4105-930D-FE4BA60E9E57}=

{59920619-B9B3-4D6F-B437-C0FF17102CD4}=

{B9539093-66F9-4246-8C50-CC417FB5D46B}=

{D8A61CBA-0FF2-4F4A-ABE8-ACC753453A49}=

{F93150AB-659D-4B7F-8DD5-F2E394F4BED2}=

{4824B5A6-3951-4ACC-A618-FAFC682AF73D}=

{82F063DF-A749-43E4-9264-536974610A9D}=

{2F1C9601-A704-4D2B-A958-762D4AD3F86A}=

{63DD761B-53A5-4AF1-BD65-BC44E6BAB8AB}=

{39F25E1A-7629-4172-A958-86CB22CB106F}=

{784B352A-CE02-4858-A85E-27BF82BA6678}=

{D089CB14-1F8F-492B-9BEA-1160ED25782C}=

{385EF990-1B35-458F-BF3D-8D8229AEDE58}=

{D23F5814-24F3-4FC2-A4C6-E729E692D69B}=

{F046A7D4-58F4-4955-8902-9847106E27C2}=

{A23CB45B-F8DD-42E4-8B73-50372E197B2F}=

{67B1FCFF-2285-42F8-9ABB-629003640D12}=

{FCD81E1E-2BFF-4143-AD5A-4ABF1DEAF3C5}=

{9B254ACC-855E-4FCA-A98D-9781EA69400E}=

{C0ACBFD1-F0EC-4D68-9328-635D2F5965CE}=

{6D16CFE2-5D15-471C-9FCD-F8072DA8D056}=

{B248D50C-4C8D-4CC7-90FC-7CFF0BB8CA5E}=

{6DC83FB3-7999-4F25-A503-FAC8A2D48DAF}=



[VSSetupWatson]

VSSWSuccessEnabled=1

VSSWSuccessHeadless=1

VSSWFailedEnabled=1

VSSWFailedHeadless=1

VSSWProdName=Microsoft .NET Framework 2.0

VSSWProdVer=8.0.50727.42_RTM_x86ret

VSSWSectionEnabled=1

VSSWProdSAID=183

VSSWInternalRelease=1

```

Any help appreciated

---

