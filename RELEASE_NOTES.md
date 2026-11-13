## Anylinux-uruntime v0.8.2

This is the Anylinux-uruntime fork of [uruntime](https://github.com/VHSgunzo/uruntime), tracking upstream version 0.8.2.

### Fork additions

- Support for a leading metadata SquashFS image. When the image at the ELF boundary is SquashFS and a DwarFS image follows it, the runtime uses the second image as the application payload. SquashFS-only thumbnailers and desktop integration tools can read `.DirIcon` and the desktop entry from DwarFS AppImages while the DwarFS payload remains the mounted application filesystem.
- The metadata sidecar is a fixed 128 KiB slot. The runtime scans up to 128 KiB past the metadata SquashFS image to find the following DwarFS payload.
- Fork identification in `--help` and `--version` output, with the upstream repository linked from the help text.
- DwarFS-only `-lite` runtimes do not gain a SquashFS reader or helper. The leading metadata image is skipped using only its superblock size field; its contents are not parsed, mounted, or extracted.

### Upstream 0.8.2 changes

- Recover automatic mounts after interrupted PID-record publication (#28).
- Fix helper-execution aborts without `/proc` and after failed exec.
- Update bundled DwarFS to 0.15.8 and squashfuse to 0.6.5.
- Refreshed runtime and xtask dependencies.
- Restored QEMU smoke tests for all foreign release artifacts.

See the [changelog](https://github.com/pkgforge-dev/Anylinux-uruntime/blob/v0.8.2/CHANGELOG.md) for the complete history.
