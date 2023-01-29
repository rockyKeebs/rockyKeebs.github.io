# Rocky Elbert Build Guide

This build guide is an overview of the building process for the Rocky Elbert. It isn't necessary to follow it, but beginners might want to as it'll help make the process much easier. The order of the steps is quite important, so I would recommend skimming through the guide even if you don't plan to follow it closely.

# Things you will Need

Most of the necessary materials come with the Rocky Elbert kit, but you will still need to source a few yourself.

## Included items:

![included items](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/included_items.jpg?v=1621153273)

1. 6 M2.5 Spacers

2. 12 M2.5 Screws

3. 4 Mill-Max Sockets

4. Reset Switch

5. Diodes

6. Bumpons

7. Plate

8. Base

9. PCB

## Non-included items:

![non-included items](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/non-included_items.jpg?v=1621153323)

1. Switches

2. Stabilizers

3. Keycaps

4. Pro micro

5. USB cable

6. Soldering iron

7. Solder

8. Tweezers

9. Electrical tape

10. Flush cutters

11. Phillips head screwdriver

## Optional items:

![optional items](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/optional_items.jpg?v=1621153355)

1. Acrylic layers

2. Mill-Max sockets

3. Painter's tape

# Flashing the Pro Micro

Pro micros don't come with the firmware that lets them act as a keyboard, so we'll need to flash ours with QMK. In this step, we'll need the pro micro, tweezers, and a USB cable. We'll also need to download QMK Toolbox, which can be found [here](https://github.com/qmk/qmk_toolbox/releases). Download and install the latest version that's compatible with your computer and open it up. It should look something like this:

![Picture of QMK toolbox UI](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/qmk_toolbox.png?v=1621145624)

Download the [hex file](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/rocky_elbert_via.hex?v=1640983287) that contains the firmware of the keyboard and load it into QMK Toolbox by click open and selecting the file. Check the box labeled "Auto-Flash." Now plug in your pro micro and reset it by connecting the pads labeled GND and RST with your tweezers like this:

![tweezers connect GND and RST pins on pro micro](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/pro_micro_reset_00447c5d-4a49-4306-bd13-d236603a11d5.jpg?v=1621148320)

The console output should now start to edit the data on the pro micro. Once it's done, it'll tell you that the flashing was successful. That's it; you've flashed a pro micro! Technically, you can now continue to the next step, but I would recommend testing the pro micro, which we'll go over next.

We'll start by installing VIA [here](https://github.com/the-via/releases/releases). VIA is a super helpful program that lets you easily change the keymap of compatible keyboards. You can also do this using QMK, but this requires some coding knowledge, and the pro micro needs to be flashed every time you change the keymap. VIA, on the other hand, lets you change the keymap on the fly.

Download the [VIA JSON](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/rocky_elbert.json?v=1640983279) file for the Rocky Elbert. Open VIA, select File > Import Keymap, and select the JSON file. VIA should now detect that the Rocky Elbert is connected:

![picture of the configure tab of VIA](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/via_configure.png?v=1621150748)

Navigate to the key tester tab and short the pro micro pads A3 and 2. The labels of the pads can differ based on if your pro micro is a clone or you used an Elite-C, but they should always be under VCC and GND. Once you short the pads, the tab key should become pink on VIA. This means that your pro micro should be functional. There is still a chance that some of the other pins may not work, but testing every single pin is extremely tedious and usually unnecessary.

Once you're confident that your pro micro is functional, you can move on to the next step: soldering the reset switch and diodes onto the PCB.

# Soldering Reset Switch and Diodes

If this is your first time soldering, don't worry, it's easy! This guide won't go into too much detail about how to solder, but there are numerous resources online. Just take it slow and watch a lot of tutorials before starting. We'll start with the reset switch.

Take your PCB and make sure that it is oriented the correct way: the text that says "Rocky Elbert R1" should be on the bottom left of the board, the pads for the pro micro should be on the top right, and the pads labeled "reset" should be on the left. Push the reset switch into the pads. It doesn't matter which way the reset switch goes as it is reversible. It should look like this:

![reset switch in pads on PCB](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/reset_switch_placement.jpg?v=1621156545)

Turn the PCB over and solder the legs of the switch.

Now, it's time to move onto the diodes. They look like this:

![diode with pins bent at 90 degree angles](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/diode_bent.jpg?v=1621157710)

If you look closely, you'll see that the diodes have black lines on one side. This is important since diodes are directional.

Let's start putting the diodes into the PCB. Make sure that your PCB is upside down compared to the way it was when you put in the reset switch: the "Rocky Elbert R1" text should not be visible, the pro micro pads should be on the left, and the reset switch should be on the right. Each switch footprint will have two pads to its right: one circle and one square. Put the diode legs all the way through the holes and then bend the pins on the other side of the PCB so that the diode is as close to the PCB as it can be, and it doesn't fall out when flipped. **Make sure that the side of the diode with a black line is on the side of the circle pad as shown in the picture:**

![diodes in holes with black side towards circle hole](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/diode_placement.jpg?v=1621158363)

Repeat this for all the diode pads on the PCB but skip the one that is next to the reset switch. We'll come back to this one later. Once you've finished inserting the diodes, cover each one with painter's tape like so:

![diodes on PCB with painter's tape covering them](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/diodes_tape.jpg?v=1621220204)

Now, flip the PCB over and solder all the diode legs.

We'll now solder the diode that goes next to the reset switch. Cut a small strip of electrical tape and use it to cover the pins of the reset switch. This'll ensure that there are no accidental shorts due to touching metal. You can now insert and solder the last diode like all the others.

# Pro Micro Mill-Max Sockets (Optional)

When ordering the Rocky Elbert, you had the choice to buy Mill-Max sockets. Even if you didn't, your kit will come with some to use on the switches that are above the pro micro. These will make it easier to test the PCB without risking switches already being soldered if there are any problems.

Mill-Max sockets can be a little annoying to solder as it's easy to get solder inside them, so I would recommend starting off with as little as possible and only adding more if necessary.

There are multiple ways to install Mill-Max sockets. [Here](https://www.reddit.com/r/MechanicalKeyboards/comments/cbykxw/millmax_socket_guide_pxlnght/) is a helpful guide from Reddit written by [u/pxlnght](https://www.reddit.com/user/pxlnght/) that highlights one way. Another way is explained by [u/cxmachi](https://www.reddit.com/user/cxmachi/) in his comment [here](https://www.reddit.com/r/MechanicalKeyboards/comments/cbykxw/millmax_socket_guide_pxlnght/ew62k4a?utm_source=share&utm_medium=web2x&context=3). I personally preferred u/cxmachi's method as there is no risk of ruining any switches, but you may have a different preference.

I'll guide you through my preferred method. Start by finding the pro micro pads.  Turn the PCB until the pads are on the top right. There will be two switch footprints that consist of two pads, one high and one low. Use your tweezers to put the sockets into the pads:

![mill max sockets in pcb pads](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_in_holes.jpg?v=1621236752)

Then, cover the sockets with electrical or painter's tape and push them down so they are as flush as possible with the PCB. You should see outlines of the sockets in the tape:

![mill max sockets covered in painter's tape](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_with_tape.jpg?v=1621236795)

You can now solder the sockets. **Make sure that no solder gets into the hole of the sockets.** If any does, you can use your soldering iron to push the socket out of the pad and use one of the extra Mill-Max sockets provided.

![mill max sockets soldered with no solder inside hole of socket](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_soldered.jpg?v=1621237101)

Once you've done this for both switches, you're done!

# Soldering the Pro Micro

You can now move on to soldering the pro micro. This involves two steps: soldering the headers to the pro micro and soldering the pro micro to the PCB. We'll start with the headers. Orient your pro micro so that the SMD components are facing up like so:

![pro micro with usb port and other SMD components facing upwards](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/pro_micro_orientation.jpg?v=1622423532)

Now, insert the headers into holes on the left and right side of the pro micro. Make sure that the plastic part of the header is on the same side as the SMD components.

We will now align the header so that the pins are perpendicular to the pro micro. You can do this using a breadboard if you have one, but this guide is going to go over an alternate way.

Locate the pro micro pads on your PCB and put the pins on the open side of the header through the PCB pads. It doesn't matter which way the PCB is facing in this step because we won't be soldering it yet. What I like to do here is put a piece of clay on the other side of the PCB so that the pins stay stable. This will ensure that the pins aren't bent when you try to put the pro micro into the PCB pads again later. This is what it should look like:

![pro micro with headers attached is placed in PCB pads with clay on the other side holding the headers steady](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/pro_micro_clay_orientation.jpg?v=1622424133)

Now, solder each of the pro micro's pins, and make sure not to bridge any pins together. Remove the clay and the pro micro from the PCB. We'll now solder the pro micro to the PCB. Orient the PCB so that the pro micro pads are on the top left. Insert the pro micro with the USB port facing to the outside of the PCB. Turn over the PCB and solder the remaining pro micro pins.

# Testing the PCB

It's time to test the PCB to make sure each key works. Plug in your PCB and open VIA. Navigate to the key tester tab and check the "Test Matrix" box. Use your tweezers to short the pair of pads for each switch footprint.

![screenshot of the matrix test ui from VIA](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/via_test_matrix.png?v=1622963243)

The gray keys should all turn pink. If they don't, pause here and email [support@rockykeebs.com](mailto:support@rockykeebs.com). If they do, feel free to continue.

# Soldering Mill-Max Sockets (Optional)

This part is only necessary if you ordered the Mill-Max socket add-on. Use whichever method you preferred earlier to insert and solder the sockets. However, do not put any sockets into the four spacebar switch footprints labeled 47, 48, 49, and 55. The footprints to avoid are circled in the following image:

![PCB with four spacebar switch footprints circled](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_areas_to_avoid.jpg?v=1623053760)

Once you've soldered the sockets, we can move on to the spacebar switches. At this step, you'll have to decide if you want to use a full-size or split spacebar. If you would like to use a full-size spacebar, put Mill-Max sockets into the footprint labeled 55:

![PCB with switch footprint 55 circled](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_full_space.jpg?v=1623054247)

If you want to use a split spacebar, put Mill-Max sockets into footprints 47, 48, and 49:

![PCB with switch footprints 47, 48, and 49 circled](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/mill_max_split_space.jpg?v=1623054286)

You can now solder the spacebar sockets. Once you've done that, you can put away your soldering iron; you've finished all the steps that involve soldering!

# Installing Switches

Before we can insert the switches, we need to install the stabilizers. I would highly recommend lubing your stabs with some Krytox 205g0 or dielectric grease as this will improve the sound of the keyboard. The Rocky Elbert is not compatible with plate-mount stabilizers, so make sure that yours are PCB mount. Both screw-in and snap-in stabilizers will work.

If you are using the split spacebar layout, you will need four 2u stabilizers. They need to stabilize the switches labeled 28, 30, 47, and 48:

![PCB with stabilizer cutouts for switches 28, 30, 47, and 48 circled](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/split_space_stab_location.jpg?v=1623103053)

If you're using the full-sized spacebar layout, you will need two 2u stabilizers and one 6.25u stabilizer. They will need to stabilize switches 28, 30, and 55.

![PCB with stabilizer cutouts for switches 28, 30, and 55 circled](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/full_space_stab_location.jpg?v=1623103213)

It's now time to install the switches onto the board. Take out your plate and orient it on top of the PCB so that the switch footprints are aligned on both parts. Now, elevate the plate with your finger and insert a switch on any corner. Make sure the switch is as far down as it can go. Look on the bottom of the PCB to see if both of the switch pins went through the pads. You can now solder the switch if you haven't installed hotswap sockets. It should look something like this:

![plate and PCB shown with switch inserted and flat against PCB](https://cdn.shopify.com/s/files/1/0562/3460/6759/files/switch_side_view.jpg?v=1623104889)

Repeat this for the other three corners and then fill out the rest of the keyboard. Once you've soldered the corner switches, you don't need to solder each switch individually; you can insert all the switches and then solder them all together. Make sure that you only insert switches into the correct spacebar switch footprints.

# Final Assembly

You're almost done! There's only one step left. Take out the base, standoffs, and screws. Screw the standoffs onto the base. If you bought the optional acrylic layers, slide those on the standoffs with the USB cutout on the top right. Put your PCB and plate on top of the standoffs and screw them on. Now, turn over the keyboard and put the six rubber bumpons next to the screws.

That was the final step! You can put on a keycap set of your choice and start using the board. If you have any issues, feel free to email [support@rockykeebs.com](mailto:support@rockykeebs.com). It'll probably take a little while to get used to not having a number row, but using layers with VIA or QMK will be very helpful.