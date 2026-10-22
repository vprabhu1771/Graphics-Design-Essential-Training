# Fixing Premiere Pro's "Unsupported Compression Type" Error

## What This Error Means

The **"unsupported compression type"** error means the audio or video codec inside your `.mp4` container is something Premiere Pro cannot read natively. This usually happens with files recorded via:

- Smartphones (HEVC/H.265)
- OBS/Zoom (variable framerates)
- Newer AV1 codecs

---

## Solutions to Bypass the Compression Block

### 1. Clear the Media Cache (Fixes Glitched Codec Recognition)

Sometimes Premiere Pro gets confused by previous import attempts and blocks the codec.

1. Close your current project.
2. Go to **Edit > Preferences > Media Cache** (Windows) or **Premiere Pro > Settings > Media Cache** (macOS).
3. Click the **Delete** button next to "Remove media cache files".
4. Select **Delete all media cache files** from the system and click **OK**.
5. Restart Premiere Pro.

---

### 2. Rename the Extension to `.mp5` or `.mov`

Force Premiere Pro to use a different internal demuxer to read the compression layout.

- Right-click your `.mp4` file and rename the extension to `.mov`.
- If that fails, trick the system by renaming it to `.mp5`. (This forces Premiere Pro to re-evaluate the audio/video streams from scratch).

---

### 3. Convert the File to a Standard Edit Format (Guaranteed Fix)

If the compression type is completely incompatible (like AV1 or an un-indexed variable framerate), you need to re-wrap it using a free transcoder like **HandBrake** or **VLC Media Player**.

#### Using HandBrake

1. Open HandBrake and drop your `.mp4` file in.
2. In the **Summary** tab, leave the format as **MP4**.
3. Go to the **Video** tab:
   - Set **Video Codec** to **H.264 (x264)**.
   - Change **Framerate** to **Constant Framerate (CFR)**.
4. Choose a destination path at the bottom and click **Start Encode**. The new file will import perfectly.

#### Using VLC Media Player

1. Open VLC and go to **Media > Convert / Save**.
2. Click **Add** to load your `.mp4`, then click **Convert / Save**.
3. Under **Profile**, select **Video - H.264 + MP3 (MP4)**.
4. Click the **Tools** (wrench icon) next to the profile, go to the **Audio codec** tab, check the **Audio** box, and ensure the codec is set to **MPEG Audio** or **AAC**. Click **Save**.
5. Choose your destination file name and click **Start**.

---

## Still Stuck?

Tell me:

- What device or software created this video (e.g., iPhone, OBS, an online downloader)?
- What operating system (Windows or macOS) you are using?

I can give you the exact settings to adjust on that device so this compression error doesn't happen on future recordings.
