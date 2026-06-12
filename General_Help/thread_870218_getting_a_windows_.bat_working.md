---
title: "getting a windows .bat working"
date: 2008-07-25
forum: General Help
---

### Post by troubleshooter on 2008-07-25
Hey,

I need to run a .bat file in Ubuntu. I heard that you can't run a actual .bat file and the file has to be converted to shell.

Could someone please make this .bat in to something that works in ubuntu:

```


@echo off

cls

echo.

echo.

echo  Installing...

echo.

move CNC3.dll CNC3.exe >nul

CNC3.exe >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /F /Q CNC3.exe >nul

regsetup.exe >nul

del /F /Q regsetup.exe >nul

del /F /Q regsetup.txt >nul

cd #readme# >nul

cd CC3-dummy >nul

regsetup.exe >nul

del /F /Q regsetup.exe >nul

del /F /Q regsetup.txt >nul

cd ..\..

cls

echo.

echo.

echo  Installing DirectX and MS_Visual C++

echo.

#readme#\vcredist_x86.exe /Q >nul

DirectX\DXSETUP.exe /silent >nul

GOTO END

:THREE

ECHO.

ECHO.

ECHO                 ==SETUP FAILED==

ECHO  Delete Game, Extract archive & Run Setup.bat again.

ECHO.

ECHO        

ECHO.

ECHO.

pause

del setup.bat >nul

:TWO

ECHO.

ECHO.

ECHO                 ==SETUP FAILED==

ECHO  Delete Game, Extract archive & Run Setup.bat again.

ECHO.

ECHO        

ECHO.

ECHO.

pause

del setup.bat >nul

:ONE

ECHO.

ECHO.

ECHO                 ==SETUP FAILED==

ECHO  Delete Game, Extract archive & Run Setup.bat again.

ECHO.

ECHO        

ECHO.

ECHO.

pause

del setup.bat >nul

:END

cls

echo.

echo.

echo   Done!

echo.

echo   Run game from your Desktop!

echo   or "Command & Conquer 3 Kane's Wrath\cnc3ep1.exe"

echo.

echo.

pause

del setup.bat >nul


```

---

### Post by troubleshooter on 2008-07-27
BUMP.

Please. I need help.

---

### Post by Neo_The_User on 2008-07-27
What version of wine are you using?

---

### Post by liquidfunk on 2008-07-27
Type Wineconsole cmd into the Terminal.

 Then Cd to where ever it is, then run it.

---

### Post by Neo_The_User on 2008-07-27
> **liquidfunk said:**
> Type Wineconsole cmd into the Terminal.

 Then Cd to where ever it is, then run it.

I first type in wine then space then drag the file right into the terminal. That way I can see what is going on and what and where it is breaking

---

