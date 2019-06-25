## 修改说明
1. 基于v3.12.1
2. 配置：Debug, Release, RelWithDebInfo, MinSizeRel
3. 存在两种构建系统：
  * 单配置构建系统：如make、ninja，要调整配置需要clean后重新编译
  * 多配置构建系统：如MSVC，可以配置间切换，构建中间文件仍然存在
4. CMake对多配置构建系统，输出中间文件放在target_name.dir\configuration_name目录中，而对于单配置是放在CMakeFiles\target_name.dir目录下，如果想ninja和MSVC同时使用，他们的编译中间文件是无法复用的，因此本修改版将ninja的中间文件输出目录修改成和MSVC一样。