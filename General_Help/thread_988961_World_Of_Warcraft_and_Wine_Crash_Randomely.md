---
title: "World Of Warcraft and Wine Crash Randomely"
date: 2008-11-21
forum: General Help
---

### Post by Chris_Foster on 2008-11-21
When I run World Of Warcraft, it works fine until i try to make a character. Ive just started playing, so I have to make a new character. When I try to change anything about my character, like race or class, the game crashes. If I run it from a terminal, the process doesnt close, just stops and leaves me at my desktop. I've gone through a incredible ammount of effort and Ive tried every available alternative to play world of warcraft, but wine is the only way available to me.

Here is what happened when I ran from the terminal:

```

fixme:shdocvw:PersistStreamInit_Load (0x1306f8)->(0x33e2c4)
fixme:shdocvw:OleControl_FreezeEvents (0x1306f8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1306f8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x130c88): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130c88): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130c68): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130c68): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130c68): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130c68): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x131000): WIN32_FIND_DATA is not yet filled.
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8e0a08, overlapped 0x7d8e09ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x139ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x130794)->((null) 1 0x33bc58 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 25 2 0x33bc6c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 26 2 0x33bc6c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x130794)->(0x33bca8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33bd6c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x131000)->(L"" L"" 0 0x33bda4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 29 2 0x33e9a8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x130794)
fixme:shdocvw:ClientSite_GetContainer (0x130794)->(0x33e7e8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x130794)->(0xb7dd46d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 25 2 0x33e71c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 26 2 0x33e71c (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x130794)->((null) 28 2 0x33e948 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1306f8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x149ca0)->((nil))
fixme:shdocvw:OleObject_Close (0x1306f8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
kira@Uplink:~$ fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af59c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x136a40) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x135968) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x374025c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x134768): stub

```

Then I had to CTRL-C to end the process. It doesnt look like anything is wrong, but there is a-lot of fixme's. I dont understand what im support to be fixing or what a stub is as-well. 

I hope someone can help me, as im really egar to play this game (and ive payed for 5 months credit already)

---

### Post by Chris_Foster on 2008-11-21
Nevermind to all who have the same problem. Here is a tutorial I followed:

[http://www.linuxforums.org/forum/wine/71852-world-warcraft-wine.html](http://www.linuxforums.org/forum/wine/71852-world-warcraft-wine.html)

I think it was because I didnt have some .dll files and wasnt using opengl.
But there is a rendering problem with the grass for me, still

---

