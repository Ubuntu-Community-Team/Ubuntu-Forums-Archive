---
title: "Really need help with this problem"
date: 2008-10-21
forum: General Help
---

### Post by Natpjohnson on 2008-10-21
I didn't know which forum topic to put this under because i don't know if it is a problem with WoW or Wine.  I recently installed World of Warcraft under wine using the how to.  Everything works fine but when i log into my realm the window running WoW just exits and leaves me with WoW screen residue that i have to clear off to see my desktop.  It does this with some realms and works a little with some until i hit create character and it does the same thing.  Either way when i run it through the terminal i get the same output until it exits.

```

nathaniel@nathaniel-desktop:~$ env WINEPREFIX="/home/nathaniel/.wine" wine "C:\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x12ed18)->(0x32e2c4)
fixme:shdocvw:OleControl_FreezeEvents (0x12ed18)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12ed18)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x12f360): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f700): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f6e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f6e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f6e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f6e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12f6e0): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8eaa08, overlapped 0x7d8ea9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x138ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12edb4)->((null) 1 0x32bc84 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 25 2 0x32bc98 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 26 2 0x32bc98 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12edb4)->(0x32bcd4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32bd98 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12f6e0)->(L"" L"" 0 0x32bdd0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 29 2 0x32e9a8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12edb4)
fixme:shdocvw:ClientSite_GetContainer (0x12edb4)->(0x32e7e8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12edb4)->(0xb7de26d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 25 2 0x32e71c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 26 2 0x32e71c (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12edb4)->((null) 28 2 0x32e948 (nil))
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12ed18)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1484a0)->((nil))
fixme:shdocvw:OleObject_Close (0x12ed18)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
nathaniel@nathaniel-desktop:~$ fixme:advapi:SetSecurityInfo stub
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
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x134cb8) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x133be0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf34,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x374022e4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x3004c, 0x1329e0): stub




```


I really don't know what any of that means but I'm sure some one does.  I really need this problem fixed because i haven't been able to play it in a while.  Any help is very much appreciated. Thanx

---

