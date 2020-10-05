#include <windows.h>
#include <iostream>

int main(  ) {

	std::string test = "findme";
	std::cout << "0x" << std::hex << (size_t)std::addressof(test) << std::endl;

	MEMORY_BASIC_INFORMATION mbi;

	for (size_t address = 0; VirtualQuery((PVOID)address, &mbi, sizeof mbi); address += mbi.RegionSize) {

		if (mbi.State != MEM_COMMIT) continue;
		if (mbi.Protect != PAGE_READWRITE) continue;

		for (size_t x = 0; x < mbi.RegionSize; ++x) {

			for (size_t y = 0; y < test.length(); ++y) {

				if (*(byte*)(address + x + y) != test[y])
					break;
			
				if (y == test.length() - 1) {

					std::cout << "0x" << std::hex << address + x << std::endl;

				}

			}

		}

	}

    return EXIT_SUCCESS;
	
}
