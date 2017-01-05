cmake_minimum_required(VERSION 3.0)

project(CUDACMAKETEST)

find_package(CUDA REQUIRED)
message("CUDA root dir is ${CUDA_TOOLKIT_ROOT_DIR}")
message("CUDA path is ${CUDA_INCLUDE_DIRS}")
include_directories(${CUDA_TOOLKIT_ROOT_DIR}/samples/common/inc)

find_package(Boost REQUIRED)

find_package(Eigen3 REQUIRED)
include_directories(${EIGEN_INCLUDE_DIR})

set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS} --gpu-architecture sm_60)

set(CUDASRCS cusolver_wrapper.cu)

CUDA_ADD_LIBRARY(cusolver_wrapper ${CUDASRCS})
