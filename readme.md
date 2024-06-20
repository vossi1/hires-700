# HIRES-700 - Hires graphics cart for the CBM 700  

**Copyright (c) 2024 Vossi - v.1.1**

**www.mos6509.com**

## License
This work is licensed under a Creative Commons Attribution-ShareAlike 4.0
International License. See [https://creativecommons.org/licenses/by-sa/4.0/](https://creativecommons.org/licenses/by-sa/4.0/).

**[Schematic](https://github.com/vossi1/hires-700/blob/master/hires-700.png)**

**[Parts](https://github.com/vossi1/hires-700/blob/master/parts.txt)**

**description:**

Hello, I found a home-made graphics card in a 610 a few years ago. The card had already been
patched in various places. Fortunately, I also found a note in a folder with notes on the
installation and corrections.
Now I reverse engineered it and realised that this card cannot work due to design errors :wink:

I then modified it, extended it and adapted it for the 7xx.
My new layout measuring only 10x6.7cm and runs perfectly.

I programmed the CRTC to 400 lines. Now the pixels are a bit more square.
However, as the phosphor remains lit for such an extremely long time, there is no flickering.

The 640x400 pixels of the Hires card fit with 32000 bytes exactly into the 32KB RAM of the card.
Hires graphics and text pixels are linked OR, as with the Data Becker Hires 8000. In my opinion,
this is the most usable concept!

:white_check_mark: I also coded a nice Basic Cartridge with many fast new BASIC commands!

![Andy](https://github.com/vossi1/hires-700/blob/master/photos/andy.jpg)

**details:**

The card/ram access is controlled via UserPort B.
It should also work with the 8088 or Z8000 card - but unfortunately not with the Proxa7000,
as this is also controlled via PortB. PortA is unfortunately not available (used by IEEE).

The PET700 monitor still works with 18.4kHz, but the vertical frequency is now 44Hz.
Standard characters are now 16 pixels high.
The real resolution is now 720x400, but every ninth pixel cannot be influenced. It is controlled
in text mode via the flip-flop 0 - or in graphics mode 1.
I always use the graphics mode of the 700 so that horizontal lines are continuous.
The character-set can still be switched freely via the hires card.

There are only simple standard TTLs. The board is in the Char+Screenram socket and a 74245 must
also be socketed.

![Hires-700 Card](https://github.com/hires-700/v6510/blob/master/photos/hires700.jpg)

**demos / cartridge**

The assembler demos run without a cartridge.

For the Basic demos you need my cartridge at $6000 in the expansion slot. 
The cart runs with Basic 128 and Basic 256 - it has all modified Basic routines twice,
as the Basic variants have different subroutine addresses.

If there is a Hires-Basic command after THEN, a : must be placed in front of it.
The commands are clearly visible in the Demo700 - I will write a list.
In the sprite demo you can see the sprite commands. In the font demo you can see the Hires Print
command HPRINT. In the PRINT demo you can see the UPRINT command.

![Circles](https://github.com/vossi1/hires-700/blob/master/photos/circles.jpg)

**assembling / installing:**

Charrom and Videoram must be socketed.
The video 74245 must also be socketed and plugged into the hires card.
I plug the card with the 0.45mm pins into intermediate spring contact sockets so as not to widen
the board sockets-but it also fits directly if you don't have socketed TTLs under the hires board.
The 20-pin ICs are all rotated - please note! - this was more favourable in terms of layout.
7 pins must be connected to the user port B - is labelled (also visible in the circuit diagram).
1 pin must be connected to one of the expansion connectors on pin25 (phi2).
1 pin must be connected to !QU on an IC (shown in the circuit diagram).
The last pin of the pinheader and two gates in the 7400 are reserve.
I have also successfully tested an LS for the 74ALS574.

Prototype:
![Prototype](https://github.com/hires-700/v6510/blob/master/photos/prototype.jpg)
