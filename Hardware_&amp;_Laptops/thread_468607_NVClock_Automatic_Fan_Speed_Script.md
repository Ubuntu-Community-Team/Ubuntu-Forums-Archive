---
title: "NVClock Automatic Fan Speed Script"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by Megatog615 on 2007-06-09
From: [http://gentoo-wiki.com/HARDWARE_Nvidia_Fanspeed_Auto-Adjustment](http://gentoo-wiki.com/HARDWARE_Nvidia_Fanspeed_Auto-Adjustment)

Does this script work in Ubuntu Feisty? I find the idea ingenious. It automatically increases the fan speed for NVIDIA cards depending on the GPU's temperature.

```
#!/usr/bin/python

"""Controls the fan speed of Nvidia video cards. Runs continually."""

# From http://gentoo-wiki.com/HARDWARE_Nvidia_Fanspeed_Auto-Adjustment
# To see nvidia info:  nvclock -i

import time, commands


def pauseForSeconds(dblSeconds):

    """Waits for the specified number of seconds before continuing."""

    if dblSeconds > 0:
        time.sleep(dblSeconds)


def outputFromCommand(strCmd):

    """Runs the specified command, waits for its completion, and returns the output."""

    strResult = commands.getoutput(strCmd)
    return strResult


def inStr(strWhole, strFind, lngStart = 0, fCaseSensitive = False):

    """The zeroth character is the first.  Otherwise, is same as in VBA.
    Returns -1 if strFind is not in strWhole.
    Note that lngStart parameter is 3rd parameter rather than 1st."""

    if lngStart < 0:
        lngStart = 0

    # Do a quick check to see whether case sensitivity can be turned on, which is faster.
    if not fCaseSensitive and len(strFind) == 1 and not strFind.isalpha():
        fCaseSensitive = True

    if fCaseSensitive:
        return strWhole.find(strFind, lngStart)
    else:
        return strWhole.lower().find(strFind.lower(), lngStart)


def stringBegins(strChars, strCompare, fCaseSensitive = False):

    """Returns whether strChars begins with strCompare."""

    fStringBegins = False               # Default.
    lngLen = len(strCompare)
    if lngLen > 0:
        strStart = leftString(strChars, lngLen)
        fStringBegins = stringsAreSame(strStart, strCompare, fCaseSensitive = fCaseSensitive)

    return fStringBegins


def stringEnds(strChars, strCompare, fCaseSensitive = False):

    """Returns whether strChars ends with strCompare."""

    fStringEnds = False         # Default.
    lngLen = len(strCompare)
    if lngLen > 0:
        strEnd = rightString(strChars, lngLen)
        fStringEnds = stringsAreSame(strEnd, strCompare, fCaseSensitive = fCaseSensitive)

    return fStringEnds


def stringsAreSame(str1, str2, fCaseSensitive = False):

    """Returns whether the strings are the same."""

    if fCaseSensitive:
        return str1 == str2
    else:
        return str1.lower() == str2.lower()


def midString(strChars, lngStart, lngLen = None):

    """The zeroth character is the first."""

    strMid = ''
    if lngStart >= 0 and lngStart < len(strChars):
        if lngLen == None:
            # Return everything from lngStart onwards.
            strMid = strChars[lngStart:]
        else:
            if lngLen >= 1:
                strMid = strChars[lngStart : (lngStart + lngLen)]

    return strMid


def leftString(strChars, lngLen):

    """leftString('ab', 1) returns 'a'."""

    strLeft = ''
    if lngLen >= 1:
        strLeft = strChars[0 : lngLen]

    return strLeft


def rightString(strChars, lngLen):

    """The zeroth character is the first.  Otherwise, is same as in VBA."""

    strRight = ''
    if lngLen >= 1:
        strRight = strChars[-lngLen:]

    return strRight


def rightCharRemoved(strChars):

    return rightCharsRemoved(strChars, 1)


def rightCharsRemoved(strChars, lngChars):

    """Returns the string with the specified number of characters removed from the right-hand side."""

    return (leftString(strChars, len(strChars) - lngChars))


def nvClockBin():

    return '/usr/bin/nvclock'


def main():

    # Pause on startup, otherwise may get error about not being able to open /dev/nvidia0 on bootup.
    pauseForSeconds(20)
    # Set immediately to a reasonably safe speed.
    strCmd = nvClockBin() + ' -f -F 75'
    strOutput = outputFromCommand(strCmd)

    # Run forever.
    while True:
        try:
            strCmd = nvClockBin() + ' -i'
            lngAttempt = 0
            while lngAttempt <= 15:
                lngAttempt += 1
                strBoardLine = ''
                strGPULine = ''
                strDutyCycleLine = ''

                strTempLines = outputFromCommand(strCmd)
                lstTempLines = strTempLines.split('\n')
                for strTempLine in lstTempLines:
                    if stringBegins(strTempLine, 'Board temperature:', fCaseSensitive = True):
                        strBoardLine = strTempLine
                    elif stringBegins(strTempLine, 'GPU temperature:', fCaseSensitive = True):
                        strGPULine = strTempLine
                    elif stringBegins(strTempLine, 'PWM duty cycle:', fCaseSensitive = True) \
                        or (stringBegins(strTempLine, 'Fanspeed:', fCaseSensitive = True) and stringEnds(strTempLine, '%', fCaseSensitive = True)):
                        strDutyCycleLine = strTempLine

                # Don't care about the board temperature, and some cards cannot read it.
                if strBoardLine == '':
                    strBoardLine = strGPULine

                # Sometimes the temperature lines are missing.
                if strBoardLine <> '' and strGPULine <> '' and strDutyCycleLine <> '':
                    strBoardTemp = midString(strBoardLine, inStr(strBoardLine, ':') + 1).strip()
                    strGPUTemp = midString(strGPULine, inStr(strGPULine, ':') + 1).strip()
                    strDutyCyclePerc = midString(strDutyCycleLine, inStr(strDutyCycleLine, ':') + 1).strip()

                    lngBoardTemp = int(rightCharsRemoved(strBoardTemp, 1))
                    lngGPUTemp = int(rightCharsRemoved(strGPUTemp, 1))
                    dblDutyCyclePerc = float(rightCharsRemoved(strDutyCyclePerc, 1))

                    # Sanity-check the figures - required because sometimes the temperatures are wacky.
                    if 30 <= lngBoardTemp <= 110 and 30 <= lngGPUTemp <= 110 and 9 <= dblDutyCyclePerc <= 101:
                        # Ranges are OK.
                        break

            if rightString(strBoardTemp, 1) <> 'C' or rightString(strGPUTemp, 1) <> 'C' or rightString(strDutyCyclePerc, 1) <> '%':
                print 'Video card params wrong: ' + strTempLines

            # The GPU gets hotter than the board.
            if dblDutyCyclePerc >= 96 and lngGPUTemp >= 95:
                print 'Video card is melting - temperature is ' + str(lngGPUTemp)
                # Attempt to alert the user by noise. Noise.wav and aplay are in alsa-utils ebuild.
                for lngAlertLoop in range(5):
                    strAlertOutput = outputFromCommand('/usr/bin/aplay -q /usr/share/sounds/alsa/Noise.wav')
                    pauseForSeconds(1)

            # Calculate desired fan speed based on the temperature.
            dblDutyCyclePercNew = 0
            if lngGPUTemp <= 63:
                dblDutyCyclePercNew = 55
            elif lngGPUTemp <= 70:
                dblDutyCyclePercNew = 60
            elif lngGPUTemp <= 75:
                dblDutyCyclePercNew = 64
            elif lngGPUTemp <= 80:
                dblDutyCyclePercNew = 67
            elif lngGPUTemp <= 85:
                dblDutyCyclePercNew = 75
            elif lngGPUTemp <= 89:
                dblDutyCyclePercNew = 80
            elif lngGPUTemp <= 92:
                dblDutyCyclePercNew = 85
            else:
                # Is overheating - go full speed.
                dblDutyCyclePercNew = 100

            if dblDutyCyclePercNew > 0 and (dblDutyCyclePercNew >= (dblDutyCyclePerc + 1) or dblDutyCyclePercNew <= (dblDutyCyclePerc - 1)):
                # Set new duty cycle.
                strCmd = nvClockBin() + ' -f -F ' + str(int(dblDutyCyclePercNew))
                strOutput = outputFromCommand(strCmd)
                if inStr(strOutput, 'Changing', fCaseSensitive = True) < 0:
                    print 'Could not change video card temperature: ' + strOutput

            # Sanity check on ranges.
            if not (30 <= lngBoardTemp <= 150 and 30 <= lngGPUTemp <= 150 and 9 <= dblDutyCyclePerc <= 101):
                print 'Video card ranges exceeded: ' + strTempLines
        except:
            print 'Video card daemon error: ' + strTempLines
            pauseForSeconds(60)

        # Go to sleep.
        pauseForSeconds(180)

    return 0    # To keep pychecker happy.


if __name__ == '__main__':
    main()
```

---

### Post by neptho on 2007-06-09
So long as you have the proper python libraries installed, and the nvclock binary (you may have to alter the location to match Ubuntu), it should work just fine.  Aplay is part of the alsa utilities, so ensure you install alsa-utils if you want to get the alert warning if there is very high temp for your GPU.

---

### Post by MaDRaY on 2007-06-17
Hi. Im new to Linux and Ubuntu. Im trying to get this script working under Feisty. Im able to lower the fanspeed with nvclock but I dont know how to create this script. I searched for the folders listed and cannot find (its because the script was made originally for gentoo?) If yes, how should we do in Ubuntu? Thanks in advance.

---

